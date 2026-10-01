# Flujo alternativo - Datos de retiro no coinciden

| **Nombre del escenario:** | Flujo alternativo - Datos de retiro no coinciden | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Entregar pedido | | **ID Única:** | 10 |
| **Área** | Sistema de pedidos del kiosco Sabor, control de entrega | | | |
| **Actor(es):** | Usuario de mostrador, Cliente | | | |
| **Descripción:** | Impide entregar un pedido cuando el número y la referencia informados no coinciden con el registro. | | |
| **Activar Evento:** | El cliente solicita el retiro con datos incompletos o incorrectos. **Identificadores e iniciadores de caso de uso** | | | |
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | | |

| **Pasos desempeñados (ruta alternativa/excepción)** | **Información para los pasos** |
|---|---|
| 1. El cliente informa número y referencia. | Datos declarados en el mostrador. |
| 2. El usuario consulta el pedido. | Búsqueda por identificador. |
| 3. El sistema detecta que el número, referencia o estado no coincide. | Resultado de validación y estado real. |
| 4. El sistema informa que no puede validar la entrega. | Mensaje sin revelar pedidos ajenos. |
| 5. El usuario solicita una verificación adicional o deriva la consulta al encargado. | Política de identidad y atención de reclamos. |
| 6. El sistema conserva el pedido sin cambiar su estado. | Registro activo e historial intactos. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El usuario está autenticado; existe una consulta de retiro; el sistema puede validar el pedido. |
| **Poscondiciones:** | No se entrega ni cambia el pedido; queda disponible para una nueva validación autorizada. |
| **Suposiciones:** | No se muestran detalles del pedido hasta validar los datos mínimos de retiro. |
| **Reunir requerimientos:** | RF2, RF6, RF13, RNF1, RNF4, RNF10. |
| **Aspectos sobresalientes:** | ¿Qué datos adicionales puede pedir el encargado? ¿Se registra un intento de retiro fallido? ¿Cuándo se considera abandono? |
| **Prioridad:** | Alta: protege la identificación del pedido en el punto de contacto con el cliente. |
| **Riesgo:** | Alto: una validación insuficiente puede causar entrega equivocada y pérdida de información del cliente. |
