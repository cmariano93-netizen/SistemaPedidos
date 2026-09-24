# Flujo de excepción - Pedido fuera de ventana de cancelación

| **Nombre del escenario:** | Flujo de excepción - Pedido fuera de ventana de cancelación | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Cancelar pedido | | **ID Única:** | 12 |
| **Área** | Sistema de pedidos del kiosco Sabor, control de cancelaciones | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Rechaza la cancelación de un pedido que está `listo`, `entregado` o ya `cancelado`. | | |
| **Activar Evento:** | El usuario solicita cancelar un pedido cuyo estado no habilita la operación. **Identificadores e iniciadores de caso de uso** | | | |
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. El usuario busca el pedido por su identificador. | Pedido activo o consulta histórica. |
| 2. El sistema muestra el estado vigente. | Estado `listo`, `entregado` o `cancelado`. |
| 3. El usuario solicita la cancelación. | Motivo y confirmación. |
| 4. El sistema verifica la regla y rechaza la solicitud. | Estados permitidos: `recibido` o `en preparación`. |
| 5. El sistema informa el motivo y conserva el pedido sin cambios. | Mensaje, estado e historial originales. |
| 6. El usuario deriva el reclamo al encargado si corresponde. | Política de atención posterior. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe; el estado actual fue recuperado desde el registro persistente. |
| **Poscondiciones:** | El estado, la visibilidad y el historial del pedido permanecen sin cambios; no se genera una cancelación inválida. |
| **Suposiciones:** | Un reclamo posterior no modifica el estado automáticamente y requiere la política del negocio. |
| **Reunir requerimientos:** | RF8, RF6, RF7, RNF2, RNF4, RNF7. |
| **Aspectos sobresalientes:** | ¿Debe existir un proceso de devolución o reclamo separado? ¿Puede el encargado autorizar excepciones? ¿Cómo se vincula el reclamo al historial? |
| **Prioridad:** | Alta: mantiene la integridad de las transiciones y evita inconsistencias con una orden ya entregada. |
| **Riesgo:** | Medio: el sistema queda consistente, pero una respuesta operativa inadecuada puede generar un reclamo comercial. |
