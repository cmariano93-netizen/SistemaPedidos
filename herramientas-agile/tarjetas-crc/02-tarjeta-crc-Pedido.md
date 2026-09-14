# 🎴 Tarjeta CRC: Pedido

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Pedido` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Agregar, quitar o modificar un `ItemPedido` cuando el pedido está recibido | `ItemPedido` | "Conozco mi número y referencia de retiro" | `numero` |
| Calcular el total a partir de sus ítems y pagos de personalización | `ItemPedido` | "Conozco mi fecha, estado y prioridad" | `fechaHora` |
| Cambiar de estado, cancelar y validar las transiciones permitidas | `Pago` | "Sé validar mi ciclo de vida" | `estado` |
| Registrar el pago asociado y conservar el pedido cancelado para su trazabilidad | `Usuario`, `Pago` | "Sé conocer mi importe total" | `total` |