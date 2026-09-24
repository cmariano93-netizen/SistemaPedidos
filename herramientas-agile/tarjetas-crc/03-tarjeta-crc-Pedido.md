# 🎴 Tarjeta CRC: Pedido

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Pedido` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Agregar, quitar o modificar un `ItemPedido` según el estado permitido | `ItemPedido`, `PersonalAtencion` | "Sé qué cambios permite mi estado" | `estado` |
| Calcular el total a partir de sus ítems y pagos de personalización | `ItemPedido`, `Personalizacion` | "Conozco mis ítems y sé cuánto valen" | `total` |
| Cambiar de estado, cancelar y conservar el historial del pedido | `Cocina`, `Encargado` | "Sé validar mi ciclo de vida" | `estado` |
| Registrar el pago asociado al pedido | `Pago`, `Cliente` | "Sé cuál es el importe que debo cobrar" | `numero` |
