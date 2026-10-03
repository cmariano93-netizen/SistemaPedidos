# Principio de Inversión de Dependencias (DIP)

## Propósito
El **Principio de Inversión de Dependencias (DIP)** establece que los módulos de alto nivel, donde viven las reglas del negocio, no deben depender directamente de detalles de bajo nivel, como una base de datos, una terminal de cobro o un medio de comunicación. Ambos deben depender de abstracciones estables, y las implementaciones concretas deben cumplir esos contratos.

Aplicarlo no significa crear interfaces para todas las clases. En el Kiosco "Sabor", `Pedido`, `ItemPedido`, `Producto`, `Personalizacion` y `Pago` son conceptos del dominio. Sus colaboraciones entre sí representan el negocio y no necesitan ocultarse tras interfaces solo por ser dependencias concretas.

## Dependencias del diseño actual
Las tarjetas CRC identifican estas colaboraciones concretas:

| Clase | Colaboradores concretos indicados por las CRC | Evaluación DIP |
|---|---|---|
| `PersonalAtencion` | `Pedido`, `Producto`, `Personalizacion`, `Cocina` | Los primeros tres son conceptos del dominio. La interacción directa con `Cocina` acopla el envío del pedido a una forma particular de recepción. El diseño tampoco expresa contratos para consultar el catálogo o guardar pedidos. |
| `Cocina` | `Pedido`, `PersonalAtencion`, `ItemPedido`, `Producto` | `Pedido`, `ItemPedido` y `Producto` son datos y reglas del dominio que cocina necesita interpretar. Depender de `PersonalAtencion` para recibir pedidos une dos roles que pueden comunicarse mediante un contrato. |
| `Pedido` | `ItemPedido`, `Personalizacion`, `PersonalAtencion`, `Cocina`, `Encargado`, `Pago`, `Cliente` | `ItemPedido`, `Personalizacion` y `Pago` son colaboradores del dominio. Las referencias a roles (`PersonalAtencion`, `Cocina`, `Encargado` y `Cliente`) no deberían ser necesarias para que `Pedido` aplique sus propias reglas y transiciones. |
| `Pago` | `Pedido`, `Cliente` | `Pedido` es la entidad cuyo total se valida; esta relación pertenece al dominio. `Cliente` representa al actor que abona, pero no es necesario que la entidad que registra un pago dependa del actor. El tipo concreto del procesador de cobro no aparece en la CRC ni debe incorporarse a `Pago`. |

El boceto también muestra responsabilidades como `enviarPedidoACocina()`, `recibirPedido()`, `registrarPago()` y `calcularTotal()`. No incluye persistencia ni proveedores concretos de cobro; esos detalles se proponen como puntos de extensión, en lugar de atribuirlos retrospectivamente a las tarjetas.

## Abstracciones propuestas

### Comunicación con cocina
`IRecepcionPedidos` define el contrato para recibir un pedido, manteniendo la responsabilidad de `Cocina` de recibir pedidos enviados para preparación. `Cocina` puede implementar este contrato, y en el futuro otra implementación podría adaptar una pantalla o una impresora de comandas. `PersonalAtencion` depende del contrato y conserva los nombres de sus responsabilidades: registrar, modificar y enviar el pedido a cocina.

### Catálogo y almacenamiento
`ICatalogoProductos` permite que `PersonalAtencion` obtenga los `Producto` disponibles sin acoplarse a cómo se administra el catálogo. `IRepositorioPedidos` abstrae guardar y recuperar pedidos, incluidos los activos y el historial. Puede ser implementado por un repositorio en memoria o uno conectado a una base de datos.

Estas interfaces no reemplazan a `Producto` ni a `Pedido`: devuelven y almacenan las entidades CRC existentes. `Cocina` continúa interpretando `Pedido`, `ItemPedido` y `Producto`, que son parte del lenguaje del dominio.

### Procesamiento del pago
`Pago` conserva los datos del pago (`monto`, `fechaHora` y `formaPago`) y su vínculo con `Pedido`. No conoce una terminal, una pasarela ni una implementación concreta de cobro. Un servicio de aplicación `GestorPago` coordina el proceso a través de `IProcesadorPago` y guarda el resultado mediante `IRepositorioPedidos`; implementaciones como `ProcesadorEfectivo` o `ProcesadorQR` cumplen el contrato.

`GestorPago` es un coordinador de aplicación añadido para ubicar la integración externa. No reemplaza a `Pago`, no cambia las tarjetas CRC y no mueve a la entidad `Pedido` la responsabilidad de comunicarse con una pasarela. Las reglas del dominio siguen validando que el importe abonado sea coherente con el total.

## Inyección de dependencias por constructor
Las implementaciones concretas se seleccionan en el punto de composición de la aplicación y se entregan a los coordinadores al crearlos. Conceptualmente, las dependencias son:

| Receptor | Contratos recibidos por constructor | Motivo |
|---|---|---|
| `PersonalAtencion` | `IRepositorioPedidos`, `ICatalogoProductos`, `IRecepcionPedidos` | Registrar y modificar pedidos, consultar productos y enviarlos a cocina sin depender de implementaciones concretas. |
| `Cocina` | `IRepositorioPedidos` | Consultar pedidos pendientes y actualizar su estado sin conocer el mecanismo de almacenamiento. El pedido y sus ítems siguen siendo entidades del dominio. |
| `GestorPago` | `IProcesadorPago`, `IRepositorioPedidos` | Procesar el cobro y persistir el registro sin acoplar el flujo a un proveedor ni a una base de datos. |

No se inyectan repositorios ni procesadores externos dentro de `Pedido` o `Pago`: sus responsabilidades CRC describen entidades de dominio, no servicios de infraestructura. `Pedido` sigue controlando su estado, sus ítems y el registro del pago asociado; `Pago` mantiene sus datos.

## Beneficios en el Kiosco "Sabor"
* **Extensibilidad (RNF8):** se puede sustituir el almacenamiento, el catálogo, el canal de recepción en cocina o el procesador de pago sin reescribir las reglas de `Pedido`.
* **Pruebas aisladas:** los coordinadores pueden recibir implementaciones de prueba de los contratos; no hace falta conectar una base de datos, una impresora o un proveedor de cobro.
* **Menor acoplamiento entre roles:** `PersonalAtencion` y `Cocina` se relacionan mediante el contrato de recepción de pedidos, no mediante conocimiento mutuo de detalles de implementación.
* **Reglas protegidas (RNF7):** las entidades continúan siendo responsables de validar sus operaciones; la inversión de dependencias no habilita a las capas externas a cambiar directamente su estado.

## Diagrama de clases
El diagrama conserva las clases y los nombres del boceto y las tarjetas CRC, y agrega los contratos y coordinadores necesarios para mostrar los puntos de variación:

![Diagrama UML - DIP](../../diagramas/01-diagrama-clases/01-solid-05-dip.png)

Fuente PlantUML: [diagramas/01-diagrama-clases/01-solid-05-dip.puml](../../diagramas/01-diagrama-clases/01-solid-05-dip.puml).
