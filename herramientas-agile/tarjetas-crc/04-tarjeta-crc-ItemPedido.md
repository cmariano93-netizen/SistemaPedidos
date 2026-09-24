# 🎴 Tarjeta CRC: ItemPedido

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `ItemPedido` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Representar un producto y la cantidad solicitada dentro de un pedido | `Pedido`, `Producto` | "Conozco el producto que represento" | `cantidad` |
| Calcular el subtotal usando el precio unitario y la cantidad | `Producto` | "Conozco mi cantidad y precio unitario" | `subtotal` |
| Incorporar el importe adicional de sus personalizaciones | `Personalizacion` | "Sé calcular mi subtotal completo" | `precioUnitario` |
