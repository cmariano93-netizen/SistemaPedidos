# Tarjetas CRC del sistema de pedidos

Las tarjetas se elaboraron a partir del boceto corregido `diagramas/01-diagrama-clases/01-boceto-inicial-corregido.excalidraw` y del contexto funcional de `anexos/introduccion.md`.

## Índice

1. [PersonalAtencion](./01-tarjeta-crc-PersonalAtencion.md)
2. [Cocina](./02-tarjeta-crc-Cocina.md)
3. [Pedido](./03-tarjeta-crc-Pedido.md)
4. [ItemPedido](./04-tarjeta-crc-ItemPedido.md)
5. [Producto](./05-tarjeta-crc-Producto.md)
6. [Personalizacion](./06-tarjeta-crc-Personalizacion.md)
7. [Pago](./07-tarjeta-crc-Pago.md)
8. [Encargado](./08-tarjeta-crc-Encargado.md)
9. [Cliente](./09-tarjeta-crc-Cliente.md)

## Relaciones principales

- `PersonalAtencion` crea y modifica `Pedido`, y lo envía a `Cocina`.
- `Cocina` recibe y prepara `Pedido`.
- `Encargado` supervisa y cambia el estado de `Pedido`.
- `Cliente` solicita, retira y abona `Pedido`.
- `Pedido` contiene `ItemPedido` y se asocia con `Pago`.
- Cada `ItemPedido` corresponde a un `Producto` y tiene `Personalizacion`.

## Revisión crítica

- Se identificaron nueve clases en el boceto corregido: `PersonalAtencion`, `Cocina`, `Pedido`, `ItemPedido`, `Producto`, `Personalizacion`, `Pago`, `Encargado` y `Cliente`.
- No se identificaron relaciones de herencia explícitas; por eso todas las tarjetas indican `Ninguna` como superclase y subclase.
- Se descartaron `Usuario` y `Combo`, presentes en una versión anterior pero ausentes del boceto corregido.
- Se conservaron las asociaciones visibles del diagrama: atención con pedido, cocina con pedido, encargado con pedido, cliente con pedido, pedido con ítems y pago, e ítem con producto y personalización.
- Las responsabilidades se distribuyeron según los métodos y atributos del boceto: `Pedido` coordina el ciclo de vida y el total, `ItemPedido` calcula el subtotal, `Producto` informa el precio y `Personalizacion` calcula el adicional.
- Se eliminó el duplicado de `Pago` con espacio en el nombre y se conservó sólo `07-tarjeta-crc-Pago.md`.
