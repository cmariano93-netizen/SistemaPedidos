# Flujo principal - Entrega validada

| **Nombre del escenario:** | Flujo principal - Entrega validada | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Entregar pedido | | **ID Única:** | 9 |
| **Área** | Sistema de pedidos del kiosco Sabor, retiro y entrega | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Identifica un pedido listo mediante su número y referencia, y registra la entrega al cliente. | | |
| **Activar Evento:** | El cliente se presenta a retirar un pedido e informa sus datos de retiro. **Identificadores e iniciadores de caso de uso** | | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El cliente informa número y referencia de retiro. | Identificador y nombre o referencia registrada. |
| 2. El usuario busca el pedido. | Consulta de pedidos activos. |
| 3. El sistema verifica coincidencia y estado `listo`. | Número, referencia, detalle y estado. |
| 4. El usuario entrega el pedido al cliente. | Comprobación visual del contenido y del destinatario. |
| 5. El usuario confirma la entrega. | Acción explícita y usuario autenticado. |
| 6. El sistema cambia el estado a `entregado` y registra fecha y responsable. | Historial de entrega y trazabilidad. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe, está activo y en estado `listo`; número y referencia están registrados y coinciden con el pedido. |
| **Poscondiciones:** | El pedido queda en estado `entregado`, deja de estar disponible como pendiente y conserva el historial de su ciclo. |
| **Suposiciones:** | La referencia de retiro es suficiente junto con el número; el pedido se entrega una sola vez. |
| **Reunir requerimientos:** | RF2, RF6, RF7, RF13, RNF1, RNF4, RNF10. |
| **Aspectos sobresalientes:** | ¿Qué evidencia de entrega se conserva? ¿Puede entregar un tercero autorizado? |
| **Prioridad:** | Alta: completa el servicio al cliente y libera el pedido del circuito activo. |
| **Riesgo:** | Alto: entregar a la persona equivocada afecta al cliente y rompe la trazabilidad del pedido. |
