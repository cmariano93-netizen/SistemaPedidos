# Flujo principal - Preparación y pedido listo

| **Nombre del escenario:** | Flujo principal - Preparación y pedido listo | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Preparar pedido | | **ID Única:** | 5 |
| **Área** | Sistema de pedidos del kiosco Sabor, cocina | | | |
| **Actor(es):** | Cocina, Usuario de mostrador | | | |
| **Descripción:** | Permite a cocina tomar un pedido recibido, prepararlo y dejarlo listo para entrega. | | |
| **Activar Evento:** | Cocina recibe la notificación automática de un pedido nuevo. **Identificadores e iniciadores de caso de uso** | | | |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. Cocina consulta la cola de pedidos recibidos. | Lista activa, identificador, prioridad e ítems. |
| 2. Cocina selecciona el pedido y comienza su preparación. | Pedido seleccionado y estado `recibido`. |
| 3. El sistema cambia el estado a `en preparación`. | Transición válida e historial. |
| 4. Cocina prepara los productos según el detalle y personalizaciones. | Comanda completa y observaciones. |
| 5. Cocina marca el pedido como listo. | Confirmación de finalización. |
| 6. El sistema cambia el estado a `listo` y notifica a mostrador. | Estado actualizado y aviso de disponibilidad. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Cocina está autenticada; el pedido existe en la cola; el detalle y las personalizaciones están disponibles; la comunicación interna está operativa. |
| **Poscondiciones:** | El pedido queda en estado `listo`, con historial de transiciones y visible para entrega; ya no admite modificaciones. |
| **Suposiciones:** | Cocina confirma el inicio y fin de preparación desde una pantalla compartida. |
| **Reunir requerimientos:** | RF5, RF6, RF7, RNF1, RNF3, RNF5, RNF10. |
| **Aspectos sobresalientes:** | ¿La prioridad reordena automáticamente la cola? ¿Se requiere registrar tiempos de inicio y fin? ¿Qué ocurre si falta un ingrediente? |
| **Prioridad:** | Alta: conecta el registro con la entrega y determina cuándo un pedido puede retirarse. |
| **Riesgo:** | Alto: un estado incorrecto o una comanda desactualizada puede provocar preparación errónea y reclamos. |
