# Flujo principal - Cancelación autorizada

| **Nombre del escenario:** | Flujo principal - Cancelación autorizada | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Cancelar pedido | | **ID Única:** | 11 |
| **Área** | Sistema de pedidos del kiosco Sabor, cancelación lógica | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Cancela un pedido en estado `recibido` o `en preparación` sin eliminar su registro histórico. | | |
| **Activar Evento:** | El cliente solicita cancelar un pedido y el usuario consulta su estado. **Identificadores e iniciadores de caso de uso** | | | |
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El usuario busca el pedido activo. | Identificador y lista de pedidos activos. |
| 2. El sistema muestra el detalle y estado actual. | Ítems, total, referencia y estado. |
| 3. El usuario solicita la cancelación e informa el motivo. | Motivo y confirmación del cliente. |
| 4. El sistema verifica que el estado sea `recibido` o `en preparación`. | Regla de cancelación. |
| 5. El usuario confirma la operación. | Confirmación explícita. |
| 6. El sistema cambia el estado a `cancelado`, lo quita de activos y conserva el historial. | Transición, fecha, responsable, motivo e historial. |
| 7. El sistema notifica la cancelación a cocina si el pedido estaba en preparación. | Aviso interno de detención. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; el pedido existe y está activo; su estado es `recibido` o `en preparación`; se puede registrar el motivo. |
| **Poscondiciones:** | El pedido queda `cancelado`, no aparece en activos, conserva su información histórica y cocina recibe el aviso cuando corresponde. |
| **Suposiciones:** | La cancelación no elimina físicamente el pedido ni sus pagos asociados; las devoluciones siguen una política independiente. |
| **Reunir requerimientos:** | RF8, RF6, RF7, RNF2, RNF4, RNF5, RNF10. |
| **Aspectos sobresalientes:** | ¿Quién autoriza devoluciones? ¿Se permite cancelar cuando ya hay pago? ¿La cocina debe confirmar que detuvo la elaboración? |
| **Prioridad:** | Alta: evita producir o entregar pedidos que el cliente ya no requiere y mantiene el historial. |
| **Riesgo:** | Alto: una cancelación mal aplicada puede perder auditoría, generar desperdicio o dejar a cocina trabajando una orden anulada. |
