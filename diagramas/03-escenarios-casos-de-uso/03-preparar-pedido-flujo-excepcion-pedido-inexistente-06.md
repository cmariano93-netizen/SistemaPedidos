# Flujo de excepción - Pedido inexistente en cocina

| **Nombre del escenario:** | Flujo de excepción - Pedido inexistente en cocina | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Preparar pedido | | **ID Única:** | 6 |
| **Área** | Sistema de pedidos del kiosco Sabor, sincronización con cocina | | | |
| **Actor(es):** | Cocina, Usuario de mostrador | | | |
| **Descripción:** | Evita preparar o cambiar el estado de una orden cuyo identificador no está disponible en el sistema. | | |
| **Activar Evento:** | Cocina intenta abrir un pedido recibido desde la cola o mediante su identificador. **Identificadores e iniciadores de caso de uso** | | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. Cocina selecciona o ingresa el identificador del pedido. | Número informado por mostrador o notificación recibida. |
| 2. El sistema busca el pedido. | Repositorio de pedidos activos e historial. |
| 3. El sistema no encuentra el pedido o detecta una inconsistencia de sincronización. | Resultado de búsqueda y detalle del error. |
| 4. El sistema bloquea el cambio de estado y notifica a mostrador. | Alerta de sincronización; ningún pedido se crea automáticamente. |
| 5. Mostrador verifica el registro y reenvía la notificación o corrige el incidente. | Pedido original, trazabilidad y canal interno. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Cocina tiene acceso al sistema; existe un identificador recibido, aunque puede estar desactualizado. |
| **Poscondiciones:** | No cambia ningún estado ni se prepara una orden no identificada; el incidente queda comunicado para resolución. |
| **Suposiciones:** | La comunicación interna permite reintentar sin duplicar el pedido. |
| **Reunir requerimientos:** | RF5, RF6, RF7, RNF1, RNF2, RNF5, RNF10. |
| **Aspectos sobresalientes:** | ¿Debe existir una bandeja de reintentos? ¿Quién puede resolver la inconsistencia? ¿Debe generarse una alerta operativa? |
| **Prioridad:** | Alta: evita que cocina trabaje con información no trazable durante la operación. |
| **Riesgo:** | Alto: la pérdida de sincronización puede causar pedidos omitidos, duplicados o entregas incorrectas. |
