# Flujo principal - Registro de pedido exitoso

| **Nombre del escenario:** | Flujo principal - Registro de pedido exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Registrar pedido | | **ID Única:** | 1 |
| **Área** | Sistema de pedidos del kiosco Sabor, alta de pedidos | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Permite registrar un pedido con productos disponibles, cantidades, personalizaciones y referencia de retiro. | | | |
| **Activar Evento:** | El cliente solicita un pedido en mostrador y el usuario inicia la opción de nuevo pedido. | **Identificadores e iniciadores de caso de uso** | | |

|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El usuario solicita registrar un nuevo pedido. | Pantalla de alta de pedido y sesión habilitada del usuario. |
| 2. El sistema muestra el catálogo disponible. | Productos, precios vigentes y disponibilidad. |
| 3. El usuario agrega productos, cantidades y personalizaciones. | Ítems seleccionados, cantidades positivas y observaciones del cliente. |
| 4. El usuario ingresa el nombre o referencia de retiro. | Referencia que permite identificar al cliente. |
| 5. El sistema valida los datos y calcula el total. | Reglas de catálogo, cantidades, personalizaciones y precio histórico del ítem. |
| 6. El usuario confirma el pedido. | Resumen del pedido y total a confirmar. |
| 7. El sistema genera un identificador único, guarda el pedido en estado `recibido` y lo envía a cocina. | Pedido, historial, identificador y notificación interna a cocina. |
| 8. El sistema muestra la confirmación. | Número de pedido, referencia y total. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario de mostrador está autenticado; el catálogo está disponible; existen productos seleccionables; el servicio de persistencia está operativo. |
| **Poscondiciones:** | Existe un pedido único en estado `recibido`, con ítems, personalizaciones, referencia, total y precios históricos; la orden fue enviada a cocina. |
| **Suposiciones:** | El cliente informa una referencia comprensible; el identificador es generado por el sistema y no se reutiliza. |
| **Reunir requerimientos:** | RF1, RF2, RF3, RF5, RNF1, RNF2, RNF6, RNF10. |
| **Aspectos sobresalientes:** | ¿La confirmación debe imprimirse o enviarse digitalmente? ¿Se permite registrar sin referencia de retiro? ¿Cómo se informa una caída de la comunicación con cocina? |
| **Prioridad:** | Alta: es la entrada principal al ciclo del pedido y habilita preparación, cobro y entrega. |
| **Riesgo:** | Alto: un error puede duplicar pedidos, alterar el total o perder la trazabilidad entre mostrador y cocina. |
