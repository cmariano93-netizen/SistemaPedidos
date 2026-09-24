# Índice de diagramas de casos de uso

## Diagrama integrado del sistema

- [Código PlantUML](./02-diagrama-casos-uso.puml)

El diagrama representa el sistema de pedidos completo dentro de un único límite de sistema, porque el alcance es acotado y los casos de uso comparten el flujo entre mostrador y cocina.

## Actores

- **Usuario de mostrador:** registra, modifica, consulta, prioriza, cobra, identifica y entrega pedidos.
- **Cocina:** recibe y prepara pedidos, actualiza sus estados y consulta los pedidos activos.

## Casos de uso incluidos

- Registrar y modificar pedidos.
- Agregar o quitar productos.
- Modificar personalizaciones.
- Calcular el total del pedido.
- Enviar pedidos a cocina y preparar pedidos.
- Consultar y cambiar el estado de pedidos.
- Cancelar y priorizar pedidos.
- Identificar y entregar pedidos para retiro.
- Cobrar cuentas y registrar pagos.

## Relaciones UML destacadas

Las relaciones `<<include>>` representan comportamientos obligatorios dentro de otros casos de uso. Por ejemplo, registrar un pedido incluye calcular su total y enviarlo a cocina; cobrar una cuenta incluye identificar el pedido, calcular el total y registrar el pago.

## Fuente funcional

- [Contexto funcional y requisitos](../../anexos/introduccion.md)
