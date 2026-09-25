# 🎴 Tarjeta CRC: Pago

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `Pago` | | |
| **Superclase:** | `Ninguna` | | |
| **Subclase:** | `Ninguna` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Registrar el importe efectivamente abonado y la forma de pago | `Pedido`, `Cliente` | "Conozco el pedido que estoy liquidando" | `monto` |
| Validar que el pago sea coherente con el total del pedido | `Pedido` | "Conozco la fecha y el total que debo validar" | `fechaHora` |
| Informar el resultado del registro del pago | `Pedido` | "Sé identificar mi forma de pago" | `formaPago` |