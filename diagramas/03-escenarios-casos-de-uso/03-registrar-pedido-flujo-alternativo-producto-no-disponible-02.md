# Flujo alternativo - Producto no disponible

| **Nombre del escenario:** | Flujo alternativo - Producto no disponible | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Registrar pedido | | **ID Única:** | 2 |
| **Área** | Sistema de pedidos del kiosco Sabor, validación de alta | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Evita confirmar un pedido cuando un producto solicitado dejó de estar disponible durante la carga. | | |
| **Activar Evento:** | El usuario intenta agregar o confirmar un producto que el catálogo informa como no disponible. **Identificadores e iniciadores de caso de uso** | | |

|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. El usuario agrega el producto al pedido. | Producto seleccionado y cantidad solicitada. |
| 2. El sistema consulta nuevamente disponibilidad. | Catálogo actualizado y stock habilitado. |
| 3. El sistema informa que el producto no está disponible y bloquea su incorporación. | Mensaje de validación; no se crea un ítem inválido. |
| 4. El cliente elige otro producto o abandona el pedido. | Catálogo disponible y decisión del cliente. |
| 5. Si elige otro producto, el usuario continúa desde el paso 3 del flujo principal; si abandona, el sistema descarta el borrador. | Borrador sin persistir. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; existe un pedido en edición; el sistema puede consultar el catálogo actualizado. |
| **Poscondiciones:** | No se registra un pedido con el producto no disponible; el borrador se corrige o se descarta sin duplicar información. |
| **Suposiciones:** | La disponibilidad puede cambiar entre la consulta inicial y la confirmación. |
| **Reunir requerimientos:** | RF1, RF3, RNF1, RNF2, RNF3. |
| **Aspectos sobresalientes:** | ¿Debe sugerirse un reemplazo? ¿Se reserva stock durante la edición? ¿El producto agotado se oculta o se muestra con esa marca? |
| **Prioridad:** | Alta: evita registrar pedidos imposibles de preparar y reduce errores en hora pico. |
| **Riesgo:** | Medio: no compromete dinero si se bloquea antes de confirmar, pero puede afectar la experiencia y el tiempo de atención. |
