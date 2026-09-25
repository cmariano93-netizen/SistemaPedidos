# Flujo alternativo - Pago rechazado

| **Nombre del escenario:** | Flujo alternativo - Pago rechazado | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Cobrar cuenta | | **ID Única:** | 8 |
| **Área** | Sistema de pedidos del kiosco Sabor, validación de pagos | | | |
| **Actor(es):** | Usuario de mostrador, Cliente, Medio de pago | | | |
| **Descripción:** | Gestiona el rechazo del medio de pago sin registrar un cobro aprobado ni duplicar la operación. | | |
| **Activar Evento:** | El medio de pago rechaza la autorización solicitada. **Identificadores e iniciadores de caso de uso** | | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. El usuario confirma el medio de pago. | Pedido, importe y medio seleccionado. |
| 2. El sistema solicita autorización. | Operación única y referencia del intento. |
| 3. El medio de pago rechaza la operación. | Código y motivo informado por el proveedor. |
| 4. El sistema informa el rechazo y no registra pago aprobado. | Estado del pago `rechazado` o intento fallido. |
| 5. El cliente elige otro medio o cancela el cobro. | Medio alternativo o decisión del cliente. |
| 6. Si reintenta, el flujo continúa desde el paso 3 del escenario principal. | Nuevo intento con identificador propio, sin duplicación. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El pedido existe y tiene total vigente; el usuario está autenticado; el proveedor de pago responde. |
| **Poscondiciones:** | No existe pago aprobado por el intento rechazado; el pedido y su total permanecen sin cambios. |
| **Suposiciones:** | Un reintento nunca reutiliza la misma autorización de manera ambigua. |
| **Reunir requerimientos:** | RF4, RNF2, RNF3, RNF10. |
| **Aspectos sobresalientes:** | ¿Cuántos reintentos se permiten? ¿Se registra el motivo exacto? ¿Debe bloquearse la entrega hasta obtener aprobación? |
| **Prioridad:** | Alta: permite resolver fallos de cobro sin detener ni corromper el ciclo del pedido. |
| **Riesgo:** | Alto: un manejo incorrecto puede cobrar dos veces o entregar sin pago cuando la política lo prohíbe. |
