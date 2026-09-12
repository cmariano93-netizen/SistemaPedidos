# Changelog

Registro de cambios, participación de integrantes, roles asignados y enlaces a Pull Requests e Issues de cada entrega.

---

## Actividad Obligatoria N°1

### Participantes y Roles

| Integrante | Matrícula | Rol | Issue | PR | Descripción |
| :--- | :---: | :--- | :---: | :---: | :--- |
| Mariano Costamagna | 164690 | Analista de Requerimientos | #48 | #47 | Análisis de requerimientos funcionales y no funcionales |
| Lucas Mengarelli | 164298 | Modelador de Casos de Uso | #41 | #42 | Modelado de casos de uso del sistema |
| Fernando Molina | 153090 | Diseñador de Clases Iniciales | #44 | #43 | Boceto inicial de clases con Excalidraw |
| Alexis Guardia | 158767 | Documentador y Coordinador | #39, #45, #38 | #40, #46, #37 | Estructura repositorio y documentación |

### Resumen de aportes

**Analista de Requerimientos - @alexisguardia (#48, #47)**
- Extracción de requisitos funcionales y no funcionales
- Creación de cuaderno en Notebook LM
- Documentación en `anexos/introduccion.md` con requisitos del sistema

**Modelador de Casos de Uso - @LMengarelli93 (#41, #42)**
- Identificación de actores y casos de uso
- Documentación de 5 casos de uso completos en `anexos/introduccion.md`
- Integración con Notebook LM compartido

**Diseñador de Clases Iniciales - @neith18 (#44, #43)**
- Diseño de boceto inicial en Excalidraw
- Generación de imagen PNG exportada
- Almacenamiento en `diagramas/01-diagrama-clases/`
- Actualización incluyendo `Combo` como especialización de `Producto`

**Documentador y Coordinador - @cmariano93-netizen (#39, #45, #38, #40, #46, #37)**
- Creación de estructura de carpetas y archivos
- Redacción de `README.md`, `anexos.md` e `introduccion.md`
- Introducción teórica a POO y cuatro pilares
- Revisión de todas las PRs (mínimo 4 asistidas con IA)
- Coordinación general del repositorio

### Fecha de entrega
- Habilitación de consignas: 10 de agosto 2026
- Fecha límite: 3 de septiembre 2026

### Correcciones Técnicas y Resolución de Hallazgos

**Hallazgo RC5 - Atributo `total` sin tipo de dato (RESUELTO)**
- **Severidad:** ALTA
- **Identificado en:** Clase Pedido (diagramas/boceto_inicial_clases.puml)
- **Problema:** El atributo `total` no tenía tipo de dato explícito
- **Solución aplicada:** Se actualiza a `total: Decimal` con retorno `calcularTotal(): Decimal`
- **Justificación:** Encapsulamiento fuerte y precisión en valores monetarios
- **Commit:** beb1b5b - "fix: agregar tipos de dato explícitos al atributo total en clase Pedido"
- **Estado:** ✅ RESUELTO
- **Responsable:** @fernandodanielm (Coordinador - Coordinación de correcciones)

**Revisiones de Código con IA - 12 PRs Completadas**
- Se realizaron Code Reviews asistidas por IA en todas las PRs de la Actividad:
  - PRs revisadas: #19, #20, #25, #28, #33, #34, #38, #40, #52, #55, #56, #57
  - Cada revisión incluye: hallazgos específicos, líneas señaladas, decisiones explícitas
  - Resultado: Identificación de patrones de mejora y validación de calidad técnica
- **Responsable:** @fernandodanielm (Coordinador)


