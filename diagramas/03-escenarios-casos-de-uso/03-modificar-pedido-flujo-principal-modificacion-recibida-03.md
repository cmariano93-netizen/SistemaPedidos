# Flujo principal - Modificación de pedido recibido

| **Nombre del escenario:** | Flujo principal - Modificación de pedido recibido | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Modificar pedido | | **ID Única:** | 3 |
| **Área** | Sistema de pedidos del kiosco Sabor, modificación de pedidos | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Permite agregar, quitar o modificar ítems y personalizaciones mientras el pedido aún está `recibido`. | | |
| **Activar Evento:** | El cliente solicita un cambio antes de que cocina comience la preparación. **Identificadores e iniciadores de caso de uso** | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El usuario busca el pedido por su identificador. | Número de pedido y lista de pedidos activos. |
| 2. El sistema muestra el pedido y verifica estado `recibido`. | Ítems, personalizaciones, referencia y estado vigente. |
| 3. El usuario agrega, quita o modifica productos y personalizaciones. | Cambio solicitado y cantidades válidas. |
| 4. El sistema valida las reglas y recalcula el total. | Disponibilidad, cantidades, personalizaciones y precios históricos. |
| 5. El usuario confirma la modificación. | Resumen anterior, cambios y nuevo total. |
| 6. El sistema persiste el pedido y comunica la actualización a cocina. | Historial de cambios y notificación interna. |
| 7. El sistema confirma la modificación. | Pedido actualizado y total vigente. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe; está activo y en estado `recibido`; el catálogo está disponible. |
| **Poscondiciones:** | El pedido conserva el mismo identificador, queda actualizado en estado `recibido`, con total recalculado y cambios comunicados a cocina. |
| **Suposiciones:** | El precio de cada ítem ya registrado permanece congelado; sólo los nuevos ítems toman el precio vigente. |
| **Reunir requerimientos:** | RF10, RF11, RF12, RF3, RNF1, RNF5, RNF6, RNF7. |
| **Aspectos sobresalientes:** | ¿La modificación requiere autorización del encargado? ¿Debe registrarse quién y cuándo modificó? ¿Cómo se informa al cliente el nuevo total? |
| **Prioridad:** | Alta: permite corregir pedidos antes de producción y evita cancelaciones o desperdicio. |
| **Riesgo:** | Alto: una actualización parcial o un total incorrecto puede generar diferencias entre mostrador, cocina y cobro. |
