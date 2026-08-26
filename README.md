# Sistema de Gestión de Pedidos - Kiosco "Sabor"

---

## 🎓 Carátula de Presentación

| Datos del Proyecto | Detalle Institucional |
| :--- | :--- |
| **Materia** | Diseño Orientado a Objetos |
| **Institución** | Universidad de Ciencias Empresariales y Sociales (UCES) |
| **Cuatrimestre** | 2° Cuatrimestre 2026 |
| **Grupo** | **Grupo N° 1** |

### 👥 Integrantes del Equipo

*   **Alexis Guardia**  
    *   **Matrícula:** 158767  
    *   **Carrera:** Diseño Orientado a Objetos  
    *   **Usuario GitHub:** @alexisguardia  
    *   **Rol en la AO1:** Analista de Requerimientos  
*   **Lucas Mengarelli**  
    *   **Matrícula:** 164298  
    *   **Carrera:** Diseño Orientado a Objetos  
    *   **Usuario GitHub:** @LMengarelli93  
    *   **Rol en la AO1:** Modelador de Casos de Uso  
*   **Isis Neith Escalada**  
    *   **Matrícula:** 158767  
    *   **Carrera:** Diseño Orientado a Objetos  
    *   **Usuario GitHub:** @neith18  
    *   **Rol en la AO1:** Diseñador de Clases Iniciales  
*   **Mariano Costamagna**  
    *   **Matrícula:** 164690  
    *   **Carrera:** Diseño Orientado a Objetos  
    *   **Usuario GitHub:** @cmariano93-netizen  
    *   **Rol en la AO1:** Documentador y Coordinador de Repositorio  

---

## 📝 Descripción del Proyecto

El **Sistema de Gestión de Pedidos ("SistemaPedidos")** es una solución de software diseñada para optimizar y ordenar los flujos operativos y comerciales del **Kiosco "Sabor"**. La aplicación unifica la captura ágil de pedidos en el salón, la coordinación en tiempo real con el panel de preparación en la cocina, el procesamiento multicanal de cobros (efectivo, tarjetas y transferencias) y la actualización automática del inventario de insumos.

Este sistema reemplaza los antiguos procesos informales y en papel por una arquitectura robusta, modular y escalable, desarrollada bajo el Paradigma Orientado a Objetos (POO).

---

## 🎯 Objetivo de la Actividad Obligatoria N° 1

El propósito fundamental de este primer hito es consolidar la **Ingeniería de Requerimientos** y la **Arquitectura Lógica Inicial** del software a partir de la interpretación de la documentación y audios dispersos del cliente. El equipo ha colaborado de manera distribuida bajo la metodología **GitFlow**, logrando:
1.  La extracción sistemática de un mínimo de 5 Requisitos Funcionales y 5 No Funcionales.
2.  El modelado estructurado de 5 Casos de Uso que describen los flujos clave del negocio (ruta feliz).
3.  El diseño conceptual estático del dominio mediante un diagrama de clases preliminar elaborado en Excalidraw.
4.  La validación técnica individual mediante Code Reviews asistidas por IA en Visual Studio Code.

---

## 🎨 Diagramas y Diseños

A continuación se presenta el acceso al índice portable de los materiales técnicos y complementarios del proyecto:

*   [Índice General de Anexos](./anexos/anexos.md)  
    *   *Enlace centralizado que provee la navegación hacia el análisis de requerimientos teóricos, especificaciones de casos de uso y la carpeta de diagramas editables de clases.*

---

## 📁 Estructura del Repositorio

La arquitectura del proyecto sigue el formato estricto de entrega solicitado por la cátedra:

```text
SistemaPedidos/ (Raíz)
├── .github/
│   └── PULL_REQUEST_TEMPLATE/
│       ├── feature-template.md  # Plantilla para PRs individuales (feature -> develop)
│       └── release-template.md  # Plantilla para PR de entrega oficial (release -> master)
├── README.md                    # Portada, resumen y enlace a anexos
├── changelog.md                 # Registro de contribuciones con enlaces a Issues y PRs
├── diagramas/
│   └── 01-diagrama-clases/
│       ├── 01-boceto-inicial.excalidraw  # Archivo fuente editable (Excalidraw MCP)
│       └── 01-boceto-inicial.png         # Exportación gráfica del boceto de clases
└── anexos/
    ├── anexos.md                # Índice detallado de la documentación anexa
    └── introduccion.md          # Análisis de POO, Requisitos y Casos de Uso del Kiosco

---
