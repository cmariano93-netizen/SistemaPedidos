# Especialista en Principio de Inversión de Dependencias (DIP)

## Prompt registrado

> Con base en los archivos del proyecto que te adjunté como contexto (`anexos/introduccion.md`, `01-boceto-inicial.excalidraw` y las tarjetas CRC de `herramientas-agile/tarjetas-crc/`):
>
> 1. Identifica las dependencias hacia clases concretas en el diseño actual del Kiosco "Sabor", especialmente en `Pedido`, `Pago`, `PersonalAtencion` y `Cocina`.
> 2. Propón abstracciones (interfaces o clases abstractas) para invertirlas aplicando el Principio de Inversión de Dependencias (DIP).
> 3. Indica dónde aplicar Inyección de Dependencias por constructor.
> 4. Genera el contenido para el anexo `anexos/principios-solid/05-dip.md` en Markdown conceptual, sin código Java.
> 5. Genera el código PlantUML para el diagrama de clases refactorizado `diagramas/01-diagrama-clases/01-solid-05-dip.puml`.
>
> Respeta el dominio del Kiosco "Sabor" y los nombres de métodos y atributos de las tarjetas CRC oficiales.

## Contexto analizado

- [Requisitos, estados, casos de uso y fundamentos de POO](../../anexos/introduccion.md)
- [Boceto inicial corregido en Excalidraw](../../diagramas/01-diagrama-clases/01-boceto-inicial-corregido.excalidraw)
- [Índice de tarjetas CRC](../../herramientas-agile/tarjetas-crc/tarjetas-crc.md)
- Tarjetas CRC individuales de `PersonalAtencion`, `Cocina`, `Pedido`, `ItemPedido`, `Producto`, `Personalizacion`, `Pago`, `Encargado` y `Cliente` en `herramientas-agile/tarjetas-crc/`

Se tomó como fuente de verdad de responsabilidades y colaboradores el contenido de las tarjetas CRC, y se contrastó con el boceto y los requisitos funcionales y no funcionales, especialmente RNF7 (encapsulamiento de reglas) y RNF8 (extensibilidad y modularidad).

## Respuestas obtenidas

El análisis distinguió las colaboraciones que pertenecen al modelo del negocio de las dependencias que conviene invertir:

- `Pedido` colabora con `ItemPedido`, `Personalizacion` y `Pago` como entidades del dominio. Esas dependencias expresan conceptos del pedido y no se reemplazaron por interfaces. Las referencias a los roles `PersonalAtencion`, `Cocina`, `Encargado` y `Cliente` no son necesarias para que `Pedido` aplique sus propias reglas; los actores solicitan operaciones a la entidad.
- `Pago` mantiene `monto`, `fechaHora` y `formaPago`, y se relaciona con `Pedido` para validar el importe. No conoce un proveedor, una terminal ni una pasarela de cobro.
- `PersonalAtencion` conserva sus responsabilidades CRC de registrar, modificar y enviar pedidos. Se propusieron contratos para persistencia, consulta del catálogo y recepción por cocina.
- `Cocina` conserva la interpretación de `Pedido`, `ItemPedido` y `Producto`. Su recepción puede expresarse mediante una abstracción, y la consulta/actualización de pedidos puede desacoplarse del almacenamiento.

Abstracciones propuestas:

| Abstracción | Propósito |
|---|---|
| `IRepositorioPedidos` | Guardar y recuperar pedidos, consultar los activos y conservar el historial sin fijar una tecnología de almacenamiento. |
| `ICatalogoProductos` | Consultar productos sin acoplar la atención a una implementación concreta del catálogo. |
| `IRecepcionPedidos` | Enviar pedidos a cocina a través de un contrato que puede tener distintas implementaciones. |
| `IProcesadorPago` | Aislar el proceso de cobro de la entidad `Pago` y permitir distintos medios o proveedores. |

La inyección por constructor se ubicó conceptualmente así: `PersonalAtencion` recibe `IRepositorioPedidos`, `ICatalogoProductos` e `IRecepcionPedidos`; `Cocina` recibe `IRepositorioPedidos`; y el servicio de aplicación `GestorPago` recibe `IProcesadorPago` e `IRepositorioPedidos`. `GestorPago` coordina el cobro, pero no sustituye la clase CRC `Pago`.

## Ajustes críticos realizados

- Se descartó la premisa del borrador previo de que el diseño CRC ya tenía clases concretas de infraestructura para persistencia o cobro. Las tarjetas no las incluyen; los repositorios y procesadores se documentaron como puntos de extensión propuestos, no como dependencias existentes.
- Se evitó aplicar interfaces indiscriminadamente a `Pedido`, `Pago` y a cada entidad del dominio. El DIP se enfocó en los límites variables de persistencia, catálogo, recepción en cocina y procesamiento de pagos.
- Se separó el registro del pago de su procesamiento externo. `Pago` conserva sus datos; `GestorPago` coordina el flujo usando `IProcesadorPago` y el repositorio.
- No se inyectaron servicios de infraestructura dentro de `Pedido` ni `Pago`, para mantener encapsuladas las reglas del dominio y respetar las responsabilidades de las tarjetas.
- Se mantuvieron los nombres y atributos del modelo CRC, incluido `referenciaRetiro` en `Pedido`. Los métodos del diagrama se tomaron del boceto vigente y de las responsabilidades documentadas, sin incorporar código Java.
- Se nombró el bloque PlantUML (`@startuml solid05dip`) porque el validador integrado de VS Code requería un identificador de diagrama.

## Resultado final

- Anexo conceptual: [05-dip.md](../../anexos/principios-solid/05-dip.md)
- Fuente del diagrama: [01-solid-05-dip.puml](../../diagramas/01-diagrama-clases/01-solid-05-dip.puml)

Ambos archivos pasaron la validación de errores integrada en VS Code. No se generó una imagen del diagrama porque el entorno no tenía disponible el ejecutable PlantUML CLI.
