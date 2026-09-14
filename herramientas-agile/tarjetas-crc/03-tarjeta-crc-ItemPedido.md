# 🎴 Tarjeta CRC: ItemPedido

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `ItemPedido` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Representar un producto y la cantidad solicitada dentro de un pedido | `Producto` | "Conozco el producto que represento" | `producto` |
| Calcular su subtotal usando el precio unitario y la cantidad | `Producto` | "Conozco mi cantidad y precio unitario" | `cantidad` |
| Incorporar el importe de sus personalizaciones al subtotal | `Personalizacion` | "Sé calcular mi subtotal" | `subtotal` |
| Mantener la consistencia de cantidad y precio capturado al confirmar el pedido | `Personalizacion` | "Conozco mis personalizaciones" | `precioUnitario` |