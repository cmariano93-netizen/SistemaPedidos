# Especialista en Segregación de Interfaces (ISP)

## Prompt utilizado
Leé como contexto los siguientes archivos del repositorio:

- anexos/introduccion.md
- diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw
- todas las tarjetas CRC ubicadas en herramientas-agile/tarjetas-crc/

Analizá el diseño actual de SistemaPedidos aplicando el Principio de Segregación de Interfaces (ISP).

Quiero que:

1. Identifiques conjuntos de responsabilidades y métodos ya existentes en las clases del boceto que puedan abstraerse en interfaces cohesivas y especializadas.
2. Detectes qué posible interfaz "gorda" debería evitarse porque obligaría a una clase a depender o implementar métodos que no necesita.
3. Para cada interfaz propuesta indiques:
   - nombre sugerido;
   - métodos existentes que contendría;
   - clase o clases existentes que la implementarían;
   - justificación basada en las responsabilidades actuales del dominio.
4. No inventes nuevas clases, métodos, actores ni requisitos que no estén respaldados por los archivos de contexto.
5. Evitá interfaces genéricas sin significado concreto para el dominio de Sabor Kiosco.
6. Compará especialmente estas dos posibilidades:
   - abstraer las responsabilidades de PersonalAtencion, Cocina y Encargado en interfaces especializadas;
   - segregar las distintas responsabilidades actualmente concentradas en Pedido mediante interfaces específicas.
7. Indicá ventajas, problemas o sobreingeniería que veas en cada alternativa y cuál está mejor respaldada por el diseño actual.

No modifiques archivos. Solo realizá el análisis y devolvé las propuestas para revisión crítica.

## Archivos de contexto referenciados

Para realizar el análisis con Copilot Agent Mode se indicó como contexto:

- `anexos/introduccion.md`
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
- las tarjetas CRC ubicadas en `herramientas-agile/tarjetas-crc/`

Durante el análisis, Copilot informó que el archivo `01-boceto-inicial.excalidraw` no existía con ese nombre exacto en el repositorio y utilizó en su lugar el boceto vigente `01-boceto-inicial-corregido.excalidraw`.

## Output obtenido

Copilot analizó dos alternativas principales para aplicar ISP al diseño existente.

La primera alternativa consistió en abstraer responsabilidades de `PersonalAtencion`, `Cocina` y `Encargado` mediante interfaces especializadas. Entre las propuestas aparecieron contratos relacionados con la toma y derivación de pedidos, preparación, consulta de pedidos activos y gestión del ciclo de vida.

La segunda alternativa se centró en la clase `Pedido`, identificando distintos grupos de responsabilidades dentro de sus métodos actuales:

- edición del pedido: `agregarItem()`, `quitarItem()` y `modificarItem()`;
- cálculo del total: `calcularTotal()`;
- ciclo de vida: `cambiarEstado()` y `cancelar()`;
- registro del pago: `registrarPago()`.

Copilot señaló que la segregación de `Pedido` estaba mejor respaldada por el diseño actual, ya que el boceto y las tarjetas CRC muestran en esa clase conjuntos de operaciones con finalidades diferentes.

También advirtió que no debía proponerse una única interfaz general, como `GestionPedido`, que reuniera edición, cálculo, ciclo de vida, pago y otras operaciones del sistema, porque podría obligar a los clientes a depender de métodos que no utilizan.

Además, indicó que una segregación excesiva en interfaces de un único método podía resultar innecesaria si no existía evidencia de clientes con necesidades diferenciadas.

## Ajustes realizados

El resultado de Copilot fue revisado críticamente antes de incorporarlo a la propuesta final.

Se aceptó como punto de partida la alternativa centrada en la clase `Pedido`, porque sus métodos actuales permiten identificar grupos de responsabilidades diferenciados y respaldados por el boceto, las tarjetas CRC y los requisitos del sistema.

Se realizaron los siguientes ajustes:

- Se mantuvo la agrupación de `agregarItem()`, `quitarItem()` y `modificarItem()` en una interfaz de edición, denominada `IEdicionPedido`, debido a que las tres operaciones modifican el contenido del pedido y están sujetas a las reglas de edición definidas por su estado.

- Se mantuvo la agrupación de `cambiarEstado()` y `cancelar()` en `ICicloVidaPedido`, ya que ambas operaciones participan de la administración del ciclo de vida y de las transiciones permitidas del pedido.

- Copilot inicialmente propuso separar `calcularTotal()` y `registrarPago()` en interfaces individuales. Esta fragmentación fue descartada por considerarse innecesaria para el diseño actual. Se decidió agrupar ambas operaciones en `ICobroPedido`, dado que aparecen relacionadas dentro del flujo de cobro documentado. Se dejó explícito que `calcularTotal()` también se utiliza en otros momentos del sistema y que esta agrupación se propone específicamente para el contexto de cobro.

- La alternativa de crear varias interfaces a partir de `PersonalAtencion`, `Cocina` y `Encargado` no se utilizó como solución principal. Aunque algunas de esas agrupaciones eran coherentes con las responsabilidades de las clases, su división requería asumir consumidores diferenciados que el modelo actual no muestra de manera explícita y podía introducir sobreingeniería.

- Se descartó la creación de una interfaz general como `IGestionPedido`, porque reuniría operaciones de edición, ciclo de vida y cobro en un único contrato y podría generar dependencias hacia métodos que un cliente no necesita.

- No se incorporaron nuevas clases, métodos ni actores para justificar las interfaces propuestas. En particular, no se agregó una dependencia desde una clase cliente hacia `ICobroPedido`, ya que el análisis posterior del repositorio no permitió identificar de forma inequívoca una clase existente que consuma el contrato completo.

- Durante la revisión de la justificación técnica se corrigió la redacción para diferenciar claramente los elementos existentes del boceto inicial de las interfaces incorporadas como propuesta del parcial. Las interfaces `IEdicionPedido`, `ICicloVidaPedido` e `ICobroPedido` no pertenecían al modelo original, sino que fueron diseñadas como aplicación del ISP a partir de responsabilidades ya existentes.