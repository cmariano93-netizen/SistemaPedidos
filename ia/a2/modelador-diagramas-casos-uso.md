# Modelador de diagramas de casos de uso

## Prompt utilizado

> Actuá como un Modelador de Diagramas de Casos de Uso experto en UML y PlantUML.
>
> Leé `anexos/introduccion.md` para entender el dominio, los actores y las funcionalidades del sistema. A partir de ese contexto y de los casos de uso identificados en la Actividad Obligatoria N°1, generá el código PlantUML de un diagrama de casos de uso completo del sistema.
>
> Identificá correctamente los actores, los casos de uso y sus relaciones. Agrupá los casos de uso dentro de un `rectangle` o `package` que represente el límite del sistema. Seguí la sintaxis y las buenas prácticas oficiales de PlantUML para diagramas de casos de uso.
>
> Usá un único diagrama integrado si el sistema es acotado; si separás subsistemas o módulos, justificá la decisión. Al finalizar, incluí una explicación breve de las decisiones de modelado y una revisión crítica con los hallazgos, ajustes y descartes realizados.

## Archivos de contexto consultados

- [Contexto funcional, requisitos y casos de uso](../../anexos/introduccion.md)
- [Código PlantUML generado](../../diagramas/02-casos-de-uso/02-diagrama-casos-uso.puml)
- [Índice específico de casos de uso](../../diagramas/02-casos-de-uso/diagramas_de_casos_de_uso.md)

El contexto funcional aportó los requisitos RF1 a RF13, los estados del pedido, los actores principales y los cinco casos de uso narrados: registrar pedido, cobrar cuenta, entregar pedido, cancelar pedido, preparar pedido y priorizar pedido.

## Ajustes realizados

- Se eligió un único diagrama integrado porque el alcance corresponde a un solo sistema de pedidos y los flujos comparten información entre mostrador y cocina.
- Se definieron dos actores externos: `Usuario de mostrador` y `Cocina`.
- Se agrupó el comportamiento dentro del límite `Sistema de Pedidos` mediante un `rectangle`.
- Se incorporaron los requisitos funcionales que no estaban desarrollados como casos narrados independientes: calcular total, enviar pedido a cocina, consultar pedidos activos, cambiar estado, agregar o quitar productos, modificar personalizaciones, registrar pago e identificar pedido para retiro.
- Se utilizaron relaciones `<<include>>` para comportamientos obligatorios. Por ejemplo, registrar un pedido incluye calcular el total y enviar el pedido a cocina; cobrar cuenta incluye identificar el pedido, calcular el total y registrar el pago.
- Se agregaron notas UML para expresar restricciones de negocio que no son casos de uso independientes: la cancelación sólo está permitida en estados recibido o en preparación, y la entrega requiere que el pedido esté listo.
- Los requisitos no funcionales no se modelaron como casos de uso porque describen cualidades, restricciones o condiciones operativas del sistema, no interacciones iniciadas por un actor.
- Se mantuvo `Cobrar cuenta` como caso de uso de alto nivel y `Registrar pago` como comportamiento incluido, respetando la separación entre la intención del actor y la operación interna obligatoria.

## Revisión crítica

El diagrama cubre la totalidad de los requisitos funcionales identificados y mantiene un límite de sistema claro. La principal decisión crítica fue complementar los casos de uso narrados con los RF1–RF13 para evitar que operaciones explícitas del dominio quedaran fuera del modelo. No se agregaron actores técnicos, una entidad `Sistema` ni casos de uso para requisitos no funcionales, porque no representan roles externos ni objetivos funcionales del usuario.

El archivo PlantUML quedó listo para renderizar. La validación estructural confirmó los bloques `@startuml` y `@enduml`, los dos actores, el límite del sistema y las relaciones `<<include>>`. No se ejecutó una validación mediante el compilador PlantUML porque el ejecutable no está instalado en el entorno disponible.
