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
- [Índice específico de casos de uso](../../diagramas/02-casos-de-uso/diagramas_de_casos_de_uso.md)

El contexto funcional aportó los requisitos RF1 a RF13, los estados del pedido, los actores principales y los casos de uso narrados: registrar pedido, cobrar cuenta, entregar pedido, cancelar pedido, preparar pedido y priorizar pedido.

## Artefactos generados

Se entregaron seis diagramas, uno por caso de uso, cada uno con su código PlantUML y su imagen exportada:

| Caso de uso | PlantUML | Imagen |
|---|---|---|
| Registrar pedido | [02-registrar-pedido.puml](../../diagramas/02-casos-de-uso/02-registrar-pedido.puml) | [02-registrar-pedido.png](../../diagramas/02-casos-de-uso/02-registrar-pedido.png) |
| Modificar pedido | [02-modificar-pedido.puml](../../diagramas/02-casos-de-uso/02-modificar-pedido.puml) | [02-modificar-pedido.png](../../diagramas/02-casos-de-uso/02-modificar-pedido.png) |
| Preparar pedido | [02-preparar-pedido.puml](../../diagramas/02-casos-de-uso/02-preparar-pedido.puml) | [02-preparar-pedido.png](../../diagramas/02-casos-de-uso/02-preparar-pedido.png) |
| Cobrar cuenta | [02-cobrar-cuenta.puml](../../diagramas/02-casos-de-uso/02-cobrar-cuenta.puml) | [02-cobrar-cuenta.png](../../diagramas/02-casos-de-uso/02-cobrar-cuenta.png) |
| Entregar pedido | [02-entregar-pedido.puml](../../diagramas/02-casos-de-uso/02-entregar-pedido.puml) | [02-entregar-pedido.png](../../diagramas/02-casos-de-uso/02-entregar-pedido.png) |
| Cancelar pedido | [02-cancelar-pedido.puml](../../diagramas/02-casos-de-uso/02-cancelar-pedido.puml) | [02-cancelar-pedido.png](../../diagramas/02-casos-de-uso/02-cancelar-pedido.png) |

## Ajustes realizados

- Aunque el prompt admitía un único diagrama integrado, se decidió separar el modelo en un diagrama por caso de uso. Un diagrama integrado con todos los casos incluidos y extendidos resultaba difícil de leer, y la separación permite revisar cada funcionalidad de forma independiente.
- Se definieron como actores externos `Usuario de mostrador`, `Cliente`, `Cocina` y `Entidad Financiera / Terminal de Pago`, incorporando en cada diagrama solo los que participan en ese caso de uso.
- En cada diagrama se agrupó el comportamiento dentro de un `rectangle` que representa el límite del subsistema correspondiente (por ejemplo, `Alta de Pedidos`, `Cobro de Cuenta` o `Cancelación de Pedidos`).
- Se incorporaron los requisitos funcionales que no estaban desarrollados como casos narrados independientes: calcular total, enviar pedido a cocina, consultar pedidos activos, cambiar estado, agregar o quitar productos, modificar personalizaciones, registrar pago e identificar pedido para retiro.
- Se utilizaron relaciones `<<include>>` para comportamientos obligatorios y `<<extend>>` para comportamientos opcionales o alternativos, como aplicar un descuento, rechazar una modificación o registrar un rechazo de pago. Por ejemplo, registrar un pedido incluye calcular el total y enviar el pedido a cocina; cobrar cuenta incluye identificar el pedido, calcular el total y registrar el pago.
- Se agregaron notas UML para expresar restricciones de negocio que no son casos de uso independientes: la cancelación sólo está permitida en estados recibido o en preparación, y la entrega requiere que el pedido esté listo.
- Los requisitos no funcionales no se modelaron como casos de uso porque describen cualidades, restricciones o condiciones operativas del sistema, no interacciones iniciadas por un actor.
- Se mantuvo `Cobrar cuenta` como caso de uso de alto nivel y `Registrar pago` como comportamiento incluido, respetando la separación entre la intención del actor y la operación interna obligatoria.

## Revisión crítica

En conjunto, los seis diagramas cubren los requisitos funcionales identificados y cada uno mantiene un límite de subsistema claro. La principal decisión crítica fue complementar los casos de uso narrados con los RF1–RF13 para evitar que operaciones explícitas del dominio quedaran fuera del modelo. No se agregaron actores técnicos, una entidad `Sistema` ni casos de uso para requisitos no funcionales, porque no representan roles externos ni objetivos funcionales del usuario.

Los seis archivos PlantUML quedaron listos para renderizar y se exportaron a PNG. La validación estructural confirmó en cada archivo los bloques `@startuml` y `@enduml`, los actores, el límite del subsistema y las relaciones `<<include>>` y `<<extend>>`. No se ejecutó una validación mediante el compilador PlantUML porque el ejecutable no está instalado en el entorno disponible.
