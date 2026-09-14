# 🎴 Tarjeta CRC: Producto

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Producto` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `ProductoEnvasado`, `ProductoElaborado` (si el catálogo requiere especialización) | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Proporcionar el precio vigente para una línea de pedido | `ItemPedido` | "Conozco mi nombre" | `nombre` |
| Exponer los datos comerciales necesarios para vender el producto | `ItemPedido` | "Conozco mi precio actual" | `precioActual` |
| Definir el comportamiento común de los productos y permitir una estrategia de precio especializada | `ItemPedido`, `Personalizacion` | "Sé obtener mi precio de venta" | `codigo` |