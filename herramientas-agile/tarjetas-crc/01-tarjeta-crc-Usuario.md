# Tarjetas CRC del sistema de pedidos

La siguiente tarjeta se deriva del boceto inicial de clases y de los requisitos del sistema. Se conserva la separación entre la identidad del pedido, sus líneas, el catálogo de productos, las personalizaciones y el pago. El cálculo de importes queda distribuido entre los objetos que poseen la información necesaria, evitando concentrar toda la lógica en `Usuario` o en una clase de servicio genérica.

# 🎴 Tarjeta CRC: Usuario

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Usuario` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Registrar un nuevo pedido con su referencia de retiro | `Pedido` | "Conozco mi identificador y nombre" | `id` |
| Solicitar la modificación de un pedido mientras su estado lo permita | `Pedido` | "Conozco los pedidos que gestiono" | `nombre` |
| Gestionar la interacción de atención sin calcular ni almacenar el total del pedido | `Pedido` | "Sé iniciar y solicitar operaciones del pedido" | `pedidos` |