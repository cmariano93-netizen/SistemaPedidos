# Flujo de excepción - Pedido no modificable por estado

| **Nombre del escenario:** | Flujo de excepción - Pedido no modificable por estado | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Modificar pedido | | **ID Única:** | 4 |
| **Área** | Sistema de pedidos del kiosco Sabor, control de estados | | | |
| **Actor(es):** | Usuario de mostrador, Cocina | | | |
| **Descripción:** | Rechaza una modificación cuando el pedido ya pasó de `recibido` a `en preparación`, `listo`, `entregado` o `cancelado`. | | |
| **Activar Evento:** | El usuario intenta editar un pedido cuyo estado no permite modificaciones. **Identificadores e iniciadores de caso de uso** | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. El usuario busca el pedido. | Identificador del pedido. |
| 2. El sistema recupera el estado actual. | Estado persistido y fecha de última actualización. |
| 3. El usuario solicita modificar un ítem o personalización. | Cambio solicitado. |
| 4. El sistema rechaza la operación y explica que sólo se modifica en `recibido`. | Mensaje y estado actual. |
| 5. El sistema conserva el pedido sin cambios. | Registro original e historial intactos. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe y su estado fue leído de la fuente persistente. |
| **Poscondiciones:** | No se modifica el pedido ni su total; se informa el motivo del rechazo. |
| **Suposiciones:** | El estado no puede ser alterado desde la interfaz sin utilizar una transición válida del dominio. |
| **Reunir requerimientos:** | RF10, RF11, RF12, RF7, RNF2, RNF7. |
| **Aspectos sobresalientes:** | ¿Debe ofrecerse cancelar y crear un nuevo pedido? ¿Se registra el intento rechazado para auditoría? |
| **Prioridad:** | Alta: protege la regla de negocio que evita alterar una orden ya enviada a producción. |
| **Riesgo:** | Alto: permitir el cambio produciría diferencias físicas en cocina, cobro y entrega. |
