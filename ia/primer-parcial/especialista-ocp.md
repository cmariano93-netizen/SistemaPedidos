# Especialista en Principios de Extensión - OCP

## Prompt base utilizado
ACTUA COMO UN ESPECIALISTA EN DISEÑO ORIENTADO A OBJETOS Y ARQUITECTURA DE SOFTWARE, EN PRINCIPIO SOLID. LEE LAS consignas.md DE MODO GENERAL PARA TENER UNA IDEA Y DESDE AHÍ CUMPLE LAS SIGUIENTES INSTRUCCIONES: 
1)	EN EL ARCHIVO anexos/principios-solid/02ocp.md COPIA EL ARCHIVO plantilla.md
2)	EVALUANDO LA INFORMACION DE anexos.md, diagramas/01-diagrama-clases/01-boceto-inicial-excalidraw y las tarjetas CRC de herramientas-agile/tarjetas-crc como contexto.
3)	IDENTIFICA CLASES CON LOGICA QUE PODRIAN REEMPLAZARSE CON HERENCIA O POLIMORFISMO, PROPONIENDO EXTENSIONES SIN MODIFICAR CODIGO EXISTENTE.
4)	POSTERIORMENTE DENTRO DE anexos/principios-solid/02-ocp.md COMPLETA LA PLANILLA QUE COPIASTE, RESPETANDO LOS TITULOS Y SUBTITULOS y completando y sustituyendo el desarrollo de cada uno de estos.
5)	EL DIAGRAMA QUE DEBES CREAR DEBE LLEVAR COMO NOMBRE 01-solid-02-ocp.puml y su versión exportada  01-solid-02-ocp.pgn, ESTE DIAGRAMA DEBE MOSTRAR TANTO EXTENSIBILIDAD COMO JERARQUIAS CORRECTAS Y DEBE ESTAR DENTRO DE LA CARPETA diagramas/01-diagrama-clases/

Se consultó la consigna general de la materia y se trabajó con los siguientes artefactos de contexto:

- [anexos/introduccion.md](../../anexos/introduccion.md)
- [diagramas/01-diagrama-clases/01-boceto-inicial-corregido.excalidraw](../../diagramas/01-diagrama-clases/01-boceto-inicial-corregido.excalidraw)
- [herramientas-agile/tarjetas-crc/tarjetas-crc.md](../../herramientas-agile/tarjetas-crc/tarjetas-crc.md)

Prompt resumido:

> Analiza el sistema de pedidos del kiosco y aplica el Principio Abierto/Cerrado. Identifica clases con lógica condicional que puedan modelarse mediante jerarquías o polimorfismo, proponiendo extensiones sin modificar el código existente. Considera el ciclo de vida del pedido, las formas de pago y la notificación a cocina. Luego, documenta la propuesta con una explicación técnica y un diagrama UML que muestre extensibilidad correcta y jerarquía apropiada.

## Ajustes realizados al resultado

Se revisó críticamente la propuesta inicial y se ajustó para que encaje con el modelo del dominio del proyecto:

- Se priorizaron los puntos de extensión más relevantes: `EstadoPedido`, `MetodoPago` y `CanalNotificacion`.
- Se evitó una solución demasiado abstracta que no reflejara el negocio del kiosco.
- Se mantuvo foco en la idea de “extensión sin modificación” de la lógica existente, en lugar de crear jerarquías artificiales.
- Se formalizó la explicación con ejemplos concretos sobre pedido, pago y cocina, alineados con los requisitos funcionales y no funcionales del sistema.

## Resultado final documentado

- Documento OCP: [anexos/principios-solid/02-ocp.md](../../anexos/principios-solid/02-ocp.md)
- Diagrama UML: [diagramas/01-diagrama-clases/01-solid-02-ocp.puml](../../diagramas/01-diagrama-clases/01-solid-02-ocp.puml)
- Exportación visual: [diagramas/01-diagrama-clases/01-solid-02-ocp.png](../../diagramas/01-diagrama-clases/01-solid-02-ocp.png)
