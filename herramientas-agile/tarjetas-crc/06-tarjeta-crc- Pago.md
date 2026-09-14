# 🎴 Tarjeta CRC: Pago

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Pago` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Registrar el importe efectivamente abonado y la forma de pago | `Pedido` | "Conozco el pedido que estoy liquidando" | `monto` |
| Validar que el pago sea coherente con el total del pedido | `Pedido` | "Conozco mi fecha de registro" | `fecha` |
| Informar el resultado del registro sin modificar directamente el estado interno del pedido | `Pedido` | "Sé identificar mi forma de pago" | `formaPago` |