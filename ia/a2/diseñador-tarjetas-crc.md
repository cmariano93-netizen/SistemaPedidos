# Directivas de Diseño: Análisis y Generación de Tarjetas CRC

Actuá como un experto en diseño orientado a objetos y metodologías ágiles, especializado en la técnica de **Tarjetas CRC (Clase-Responsabilidad-Colaborador)**.

## Contexto
Leé los siguientes archivos como base para tu análisis:
* `anexos/introduccion.md` (contexto funcional del sistema)
* `diagramas/01-diagrama-clases/01-boceto-inicial-corregido.excalidraw` (boceto de clases de la Actividad Obligatoria N°1)

---

## Tarea

1. **Identificación de Clases:** Identificá todas las clases principales presentes en el boceto de clases, incluyendo relaciones de herencia (superclase/subclase) si las hubiera.
2. **Generación de Tarjetas:** Para cada clase, generá una tarjeta CRC completa siguiendo exactamente la plantilla especificada abajo.
3. **Requisitos Mínimos por Tarjeta:**
   * Nombre de la clase.
   * Superclase y/o subclase, si corresponde (herencia).
   * Responsabilidades principales (qué debe saber o hacer la clase).
   * Colaboradores (otras clases con las que interactúa para cumplir cada responsabilidad).
   * Pensamiento del objeto (redactado en primera persona, ej: *"Conozco mi DNI para registrarme"*).
   * Propiedad/atributo asociado a cada responsabilidad.
4. **Estructura de Archivos:** Creá la estructura de carpetas `herramientas-agile/tarjetas-crc/` y organizá cada tarjeta en un archivo `.md` individual (uno por clase), con nombre de archivo tipo `tarjeta-crc-nombreclase.md`. Incluí además un archivo `README.md` o índice que liste todas las tarjetas generadas.
5. **Revisión Crítica:** Al finalizar, hacé una revisión crítica del resultado:
   * Verificá que cada responsabilidad tenga sentido y esté correctamente asignada a esa clase (evitando responsabilidades que en realidad pertenecen a otra clase).
   * Corregí relaciones de herencia mal planteadas o inexistentes en el boceto.
   * Ajustá colaboradores que no coincidan con las relaciones reales del diagrama de clases.
   * Descartá clases, atributos o responsabilidades que no correspondan al alcance del sistema descrito en `anexos/introduccion.md`.
   * Señalá clases que puedan estar duplicadas, mal nombradas o con responsabilidades solapadas.

---

## Plantilla de Tarjeta CRC

Cada archivo de clase debe utilizar estrictamente el siguiente formato de tabla de Markdown:

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | NombreClase | | |
| **Superclase:** | (si aplica) | | |
| **Subclase:** | (si aplica) | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Responsabilidad 1 | ClaseColaboradora | Frase en primera persona que refleje qué necesita saber/hacer | atributoRelacionado |
| Responsabilidad 2 | ClaseColaboradora | ... | atributoRelacionado |

---

## Formato de Salida Esperado

* Estructura de carpetas creada con un archivo `.md` por clase.
* Cada archivo con la tarjeta CRC completa en formato tabla markdown.
* Un índice general en `herramientas-agile/tarjetas-crc/README.md`.
* Apartado final de **"Revisión crítica"** explicando ajustes, correcciones y descartes realizados.

* **Archivos de Contexto Proporcionados a la IA:**
 - `anexos/introduccion.md` (Secciones: Requisitos Funcionales RF1-RF5 y Casos de Uso CU1-CU5)
- `diagramas/01-diagrama-clases/01-boceto-inicial.png`
- `plantilla_crc.md` (como guía de formato Markdown)
