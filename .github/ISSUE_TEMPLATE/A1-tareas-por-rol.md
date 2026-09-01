---
name: "AO1 - Tareas por Rol"
about: "Plantilla estándar y obligatoria para registrar las tareas individuales de cada integrante según su rol para la AO1."
title: "A1 - [Nombre del Rol]"
labels: "AO1, entregable, uces"
assignees: ""
---

## 👥 Registro del Integrante y Rol

*   **Nombre completo:** [Completar Nombre]
*   **Rol Asignado:** [Analista de Requerimientos / Modelador de Casos de Uso / Diseñador de Clases Iniciales / Documentador y Coordinador]
*   **Rama de Trabajo Asociada:** `feature/[nombre-del-rol]-[descripcion-corta]`

---

## 📝 1. Descripción de la Tarea del Rol
*Describa de forma resumida en qué consiste su entregable conceptual para el Kiosco "Sabor" y qué aspectos analizó críticamente de los materiales del cliente.*

---

## 🛠️ 2. Checklist de Actividades Obligatorias (Marcar con una 'x')

> Seleccione únicamente el checklist que corresponde a su **Rol Asignado** para la entrega:

### 🔍 [ ] Rol: Analista de Requerimientos
- [ ] **Estudio Crítico de Fuentes:** He analizado rigurosamente todos los correos, audios, fotos e hilos de Slack dispersos provistos por el Kiosco "Sabor".
- [ ] **Ingeniería de Requerimientos:** He redactado y clasificado secuencialmente en el archivo `introduccion.md` un mínimo de **5 Requisitos Funcionales (RF1-RF5)** y **5 No Funcionales (RNF1-RNF5)** lógicos y justificados para el negocio.
- [ ] **Cuaderno Grupal en NotebookLM:** He creado el espacio compartido del grupo en NotebookLM con todos los recursos cargados y lo he compartido con todos mis compañeros de equipo.
- [ ] **Hipervínculo de Acceso:** He incorporado el enlace web absoluto de acceso directo al NotebookLM en la sección "Requisitos iniciales del sistema" dentro de `anexos/introduccion.md`.
- [ ] **Trazabilidad de Git:** He enlazado y vinculado formalmente esta Issue con mi Pull Request asociada en GitHub para su cierre automático tras el merge.

### 👥 [ ] Rol: Modelador de Casos de Uso
- [ ] **Identificación de Comportamientos:** He determinado con precisión los actores (clientes, cajeros, cocineros, etc.) y los casos de uso lógicos del sistema.
- [ ] **Especificación de Casos de Uso:** He documentado en `anexos/introduccion.md` un mínimo de **5 Casos de Uso lógicos** cubriendo de manera estricta todos los campos obligatorios: *Nombre (en infinitivo), Actores, Descripción, Precondiciones, Poscondiciones* y un *Flujo Principal secuencial de al menos 5 pasos*.
- [ ] **Coherencia del Modelo:** He verificado que mis casos de uso modelados sean perfectamente consistentes con los análisis del cuaderno compartido de NotebookLM.
- [ ] **Trazabilidad de Git:** He enlazado y vinculado formalmente esta Issue con mi Pull Request asociada en GitHub para su cierre automático tras el merge.

### 🎨 [ ] Rol: Diseñador de Clases Iniciales
- [ ] **Boceto Inicial de Clases:** He diseñado el modelo de clases estáticas (entidades, atributos privados `-`, métodos públicos `+` y relaciones lógicas) utilizando el MCP de Excalidraw dentro de Visual Studio Code.
- [ ] **Archivo Fuente:** He guardado el archivo fuente editable con el nombre **`01-boceto-inicial.excalidraw`** dentro de la ruta `diagramas/01-diagrama-clases/`.
- [ ] **Archivo de Imagen:** He exportado el diseño a formato PNG y guardado como **`01-boceto-inicial.png`** en la misma carpeta para su previsualización rápida en GitHub.
- [ ] **Coherencia del Modelo:** He validado que el diseño de clases responda de forma consistente a los casos de uso y requerimientos definidos por mis compañeros y en el NotebookLM común.
- [ ] **Trazabilidad de Git:** He enlazado y vinculado formalmente esta Issue con mi Pull Request asociada en GitHub para su cierre automático tras el merge.

### 🛡️ [ ] Rol: Documentador y Coordinador de Repositorio
- [ ] **Arquitectura de Carpetas:** He creado de forma correcta la estructura física de directorios y archivos de la entrega en el repositorio local.
- [ ] **Gobernanza Markdown:** He verificado la prolijidad técnica de la sintaxis Markdown en todos los entregables escritos.
- [ ] **Documentación Base:** He redactado de forma completa la portada académica en `README.md` (con enlaces relativos en la sección "Diagramas y Diseños"), el índice de `anexos.md` y la introducción teórica al paradigma y los 4 fundamentos de la POO en `introduccion.md`.
- [ ] **Code Review con IA:** He coordinado y ejecutado un mínimo de **4 revisiones de código asistidas por IA** sobre las PRs de mis compañeros hacia la rama `develop`, dejando comentarios específicos y cargando *Request Changes* en las líneas correspondientes de GitHub.
- [ ] **Coordinación de Trazabilidad:** He verificado que cada integrante haya creado su Issue correctamente y que el archivo `changelog.md` se encuentre actualizado con los enlaces web absolutos correspondientes.
- [ ] **Lanzamiento final (Release):** He consolidado el trabajo integrando la rama `release/actividad-obligatoria-1` y creando la PR oficial de cierre y entrega final grupal dirigida hacia la rama protegida `master`.

---

## 📈 3. Estado de la Integración (Trazabilidad)

*   **Rama Feature:** `feature/`
*   **Pull Request Asociada:** [Pegar enlace absoluto de GitHub]
*   **changelog.md:** [ ] Confirmar con una "X" si actualizó su fila correspondiente de aportaciones en el registro de cambios.

---
*Este Issue representa una declaración formal de autoría técnica y participación individual dentro del grupo de trabajo académico.*