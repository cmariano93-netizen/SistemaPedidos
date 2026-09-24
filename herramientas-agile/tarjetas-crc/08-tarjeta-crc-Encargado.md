# 🎴 Tarjeta CRC: Encargado

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Encargado` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Supervisar los pedidos activos y su estado | `Pedido`, `Cocina` | "Sé qué pedidos requieren atención" | `Pedido` |
| Cambiar el estado de un pedido según las reglas del sistema | `Pedido` | "Sé qué transición puedo solicitar" | `Pedido` |
| Cerrar un pedido cuando se completa su entrega o cobro | `Pedido`, `Pago` | "Sé cuándo un pedido puede cerrarse" | `Pedido` |