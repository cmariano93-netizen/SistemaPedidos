# 🎴 Tarjeta CRC: Cliente

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Cliente` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Solicitar un pedido con los productos deseados | `PersonalAtencion`, `Pedido`, `Producto` | "Sé qué productos quiero pedir" | `Pedido` |
| Retirar el pedido cuando se encuentre listo | `Pedido`, `Cocina` | "Sé cuál es mi pedido para retirarlo" | `Pedido` |
| Abonar el pedido mediante una forma de pago | `Pago`, `Pedido` | "Sé cuánto debo abonar" | `Pedido` |