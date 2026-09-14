* **Prompt Utilizado:** > "Actuá como un Ingeniero de Software Experto y especialista en Diseño Orientado a Objetos (OO). 
Tu tarea es analizar el contexto del sistema (basándote en los archivos 'anexos/introduccion.md' y 'diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw') para identificar las clases principales y diseñar sus correspondientes Tarjetas CRC (Class-Responsibility-Collaborator).

### Requisitos Estrictos:
1. **Cantidad:** Debes generar tarjetas CRC para todas las clases clave utilizadas en el boceto inicial. En total, el diseño final NO debe tener menos de CINCO (5) clases clave.
2. **Revisión Crítica:** Realiza un diseño sólido y profesional. Corrige errores comunes de diseño (como bajo acoplamiento y alta cohesión), ajusta las responsabilidades adecuadamente y descarta cualquier elemento que no corresponda al dominio del sistema.
3. **Contenido de cada Tarjeta:** Cada una debe incluir obligatoriamente: Nombre de la clase, Superclase/Subclase (si aplica herencia), Pensamiento del objeto, Responsabilidades principales, Colaboraciones con otras clases y Propiedad clave.

### Estructura y Plantilla:
Debes usar estrictamente la siguiente plantilla en formato Markdown para cada una de las clases que identifiques. Sigue al pie de la letra esta estructura:

# 🎴 Tarjeta CRC: [NombreClase]

| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | `[NombreClase]` | | |
| **Superclase:** | `[Ninguna / NombreSuperclase]` | | |
| **Subclase:** | `[Ninguna / NombreSubclase]` | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| [Acción o comportamiento que realiza] | `[ClaseColaboradora]` | "Conozco mi [identificador o dato]" | `[nombreAtributo]` |
| [Cálculo o procesamiento que ejecuta] | `[ClaseColaboradora]` | "Conozco mi [estado, fecha o valor]" | `[nombreAtributo]` |
| [Gestión de estado interno de la entidad] | Ninguno | "Sé [calcular / actualizar comportamiento]" | `[nombreAtributo]` |

*(Asegúrate de adaptar las filas de la tabla según las responsabilidades reales de cada objeto, respetando el formato de los ejemplos).*
Por favor, lee los archivos de contexto mencionados y genera la propuesta completa de tarjetas CRC respetando esta estructura."


* **Archivos de Contexto Proporcionados a la IA:**
 - `anexos/introduccion.md` (Secciones: Requisitos Funcionales RF1-RF5 y Casos de Uso CU1-CU5) 
- `diagramas/01-diagrama-clases/01-boceto-inicial.png` 
- `plantilla_crc.md` (como guía de formato Markdown)
