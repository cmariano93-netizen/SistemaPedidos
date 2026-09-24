# Flujo principal - Cobro aprobado

| **Nombre del escenario:** | Flujo principal - Cobro aprobado | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Cobrar cuenta | | **ID Única:** | 7 |
| **Área** | Sistema de pedidos del kiosco Sabor, registro de pagos | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Registra el pago de un pedido y emite el comprobante correspondiente. | | |
| **Activar Evento:** | El cliente solicita abonar el pedido y el usuario inicia el cobro. **Identificadores e iniciadores de caso de uso** | | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El usuario busca el pedido. | Número de pedido y referencia de retiro. |
| 2. El sistema muestra ítems, personalizaciones y total vigente. | Detalle inmutable de precios históricos. |
| 3. El cliente selecciona el medio de pago. | Efectivo, tarjeta, QR u otro medio habilitado. |
| 4. El usuario confirma el cobro. | Medio, importe y autorización de la operación. |
| 5. El sistema valida y registra el pago. | Pago asociado al pedido, fecha, importe y estado aprobado. |
| 6. El sistema emite el comprobante. | Ticket con identificador, total, medio y resultado. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe; el total está calculado; el medio de pago está habilitado; no hay un pago aprobado previo para el mismo pedido. |
| **Poscondiciones:** | Existe un pago aprobado asociado al pedido, con comprobante y trazabilidad; el pedido conserva uno de los estados definidos (`recibido`, `en preparación`, `listo`, `entregado` o `cancelado`) sin alterar su detalle. |
| **Suposiciones:** | El pago se registra como información asociada al pedido y no agrega un estado nuevo al ciclo de vida. La política sobre el momento del cobro se mantiene independiente de la transición de estados. |
| **Reunir requerimientos:** | RF4, RF3, RNF2, RNF6, RNF10. |
| **Aspectos sobresalientes:** | ¿Se permiten pagos parciales o anulaciones? ¿Cómo se reimprime el comprobante? |
| **Prioridad:** | Alta: sin cobro no se completa la operación comercial del pedido. |
| **Riesgo:** | Alto: involucra dinero, duplicidad de cobros y necesidad de conciliación con el comprobante. |
