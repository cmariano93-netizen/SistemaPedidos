# Introducción al Diseño Orientado a Objetos e Ingeniería de Requerimientos

## 1. Descripción del Paradigma Orientado a Objetos (POO)

El **Paradigma Orientado a Objetos (POO)** es un enfoque conceptual específico y una filosofía de diseño de software que organiza los sistemas de computación en torno a entidades del mundo real modeladas como **objetos**. A diferencia del modelo estructurado o procedimental tradicional —que se basa en la descomposición del sistema en funciones independientes y flujos de ejecución de arriba hacia abajo (*Top-Down*)—, la POO unifica los datos y el comportamiento en una única estructura modular. 

Este paradigma es sumamente importante en la ingeniería de software moderna debido a que promueve:
*   **Modularidad y Cohesión:** Los objetos tienen responsabilidades claras y bien delimitadas, haciendo que el software sea más fácil de comprender y depurar.
*   **Reutilización de Código:** Permite definir plantillas genéricas (clases) para crear múltiples instancias u objetos con comportamientos comunes, reduciendo la redundancia de código.
*   **Mantenibilidad:** El aislamiento de los datos dentro del objeto garantiza que cualquier modificación posterior en sus atributos o métodos tenga un impacto mínimo en el resto del sistema.

---

## 2. Los Cuatro Fundamentos de POO Aplicados al Proyecto

A continuación, se describen con ejemplos prácticos del **Sistema de Pedidos del Kiosco "Sabor"** cómo se aplican los principios fundamentales del modelo orientado a objetos en la etapa de análisis lógico, sin utilizar código ni sintaxis de implementación compleja.

### A. Abstracción
La **Abstracción** consiste en resumir las características complejas del mundo real, capturando únicamente aquellos atributos y comportamientos que resultan esenciales y relevantes para el propósito específico del sistema de software, ignorando los detalles innecesarios.

*   **Ejemplo en el Kiosco "Sabor":** En la realidad, un producto de almacén tiene propiedades como su fecha de elaboración, lote del fabricante, dimensiones físicas, peso neto o ingredientes. Sin embargo, para nuestro sistema centrado en la **Gestión de Pedidos**, la clase **`Producto`** se abstrae para capturar únicamente los atributos comerciales e indispensables para una venta: `idProducto`, `nombre`, `precioUnitario` y `stockDisponible`.
*   **Esquema de Abstracción:**
    ```text
    [ Objeto del Mundo Real: Gaseosa Cola ] ──► [ Abstracción para Pedidos ]
    ├── Atributos Relevantes: ID, Nombre, Precio, Stock
    └── Atributos Ignorados: Peso de botella, Lote del fabricante, Temperatura
    ```

### B. Encapsulamiento (y Ocultación de Datos)
El **Encapsulamiento** es la técnica de empaquetar o reunir los atributos (datos) y las funciones miembro (métodos) que los manipulan dentro de una única estructura independiente (clase) [13, 17]. El estado interno de un objeto se define como privado (oculto) y solo puede ser accedido o modificado a través de una interfaz pública bien definida.

*   **Ejemplo en el Kiosco "Sabor":** El estado de un pedido (`Pendiente`, `En preparación`, `Listo`, `Entregado`) y el `montoTotal` son datos críticos que no deben ser modificados directamente por módulos externos al objeto. La clase **`Pedido`** encapsula estos datos haciéndolos **privados (`-`)**. Para alterar el estado, el sistema debe utilizar métodos **públicos (`+`)** como `confirmarPedido()` o `pagarPedido()`, los cuales ejecutan internamente las reglas lógicas y validaciones de caja antes de realizar la modificación.
*   **Esquema de Encapsulamiento:**
    ```text
    ┌──────────────────────────────────────────────┐
    │                Clase: Pedido                 │
    │  ┌────────────────────────────────────────┐  │
    │  │ ATRIBUTOS PRIVADOS (Ocultos)            │  │
    │  │ - idPedido, - montoTotal, - estado     │  │
    │  └───────────────────▲────────────────────┘  │
    │                      │ Acceso solo vía       │
    │  ┌───────────────────┴────────────────────┐  │
    │  │ MÉTODOS PÚBLICOS (Interfaz)            │  │
    │  │ + agregarProducto(), + pagarPedido()   │  │
    │  └────────────────────────────────────────┘  │
    └──────────────────────────────────────────────┘
    ```

### C. Herencia
La **Herencia** es el mecanismo mediante el cual una clase derivada (clase hija) adquiere de forma automática la estructura de datos (atributos) y el comportamiento (métodos) de una clase base (clase madre). Esto facilita la reutilización de código y la extensibilidad del diseño.

*   **Ejemplo en el Kiosco "Sabor":** En el kiosco interactúan distintos tipos de usuarios que comparten características básicas. Para evitar la duplicación de atributos (como nombre, DNI y correo), se crea una superclase abstracta llamada **`Usuario`**. A partir de ella se heredan las subclases **`Cliente`** (que extiende con atributos de fidelidad como `puntosAcumulados`) y **`Empleado`** (que extiende con `idLegajo` y `rol`), heredando automáticamente las propiedades de la clase base sin necesidad de volver a declararlas.
*   **Esquema de Jerarquía de Herencia:**
    ```text
                [ Superclase: Usuario ]
         (Atributos: ID, Nombre, DNI, Email)
                       ▲
                       │ (Hereda de...)
             ┌─────────┴─────────┐
             │                   │
       [ Cliente ]          [ Empleado ]
    (puntosAcumulados)    (idLegajo, rol)
    ```

### D. Polimorfismo
El **Polimorfismo** es la propiedad que permite que objetos pertenecientes a clases diferentes dentro de una misma jerarquía respondan al mismo mensaje de manera distinta. El emisor envía un estímulo genérico y cada receptor ejecuta su propia implementación.

*   **Ejemplo en el Kiosco "Sabor":** El sistema necesita procesar el cobro de pedidos con diferentes formas de pago a través de un mensaje común llamado **`procesarPago()`**. Gracias al polimorfismo, el objeto **`PagoEfectivo`** procesa el mensaje verificando el monto entregado y calculando el vuelto, mientras que el objeto **`PagoTarjeta`** procesa el mismo mensaje conectándose con el posnet para validar la transacción y almacenar el número de cupón de pago.
*   **Esquema de Polimorfismo:**
    ```text
    Mensaje genérico enviado: "procesarPago(monto)"
    ├──► Receptor: PagoEfectivo ──► Valida billetes, registra ingreso, calcula vuelto.
    └──► Receptor: PagoTarjeta  ──► Conecta pasarela, procesa cobro, almacena cupón.
    ```

---

## 3. Requisitos Iniciales del Sistema

A continuación, se documenta la lista de los requisitos de software iniciales que guían el diseño de nuestro sistema de pedidos para el kiosco.

*   **Cuaderno Grupal de NotebookLM:** [https://notebooklm.google.com/notebook/workspace-kiosco-sabor-grupo-x](https://notebooklm.google.com/notebook/workspace-kiosco-sabor-grupo-x)

### A. Requisitos Funcionales (RF)
Los requerimientos funcionales describen los servicios específicos que debe proveer el software, cómo debe reaccionar a entradas particulares y qué comportamientos debe manifestar ante escenarios definidos.

*   **RF1 (Registro de Pedidos):** El sistema debe permitir al Cajero registrar un nuevo pedido asociando los productos seleccionados del menú, las cantidades solicitadas y calculando dinámicamente el monto total a pagar.
*   **RF2 (Seguimiento de Estado):** El sistema debe actualizar e informar en tiempo real el estado de cada pedido (`Pendiente`, `En preparación`, `Listo para retirar`, `Entregado`) tanto en la pantalla del cliente como en el panel de la cocina.
*   **RF3 (Cobro y Medios de Pago):** El sistema debe permitir registrar el cobro de los pedidos admitiendo múltiples medios de pago (efectivo, tarjeta de crédito/débito y transferencia bancaria) [14].
*   **RF4 (Control de Stock de Cocina):** Al confirmarse un pedido, el sistema debe descontar automáticamente del inventario la cantidad correspondiente de ingredientes y productos terminados disponibles.
*   **RF5 (Administración de Menú):** El sistema debe permitir al Encargado del Kiosco agregar, modificar o dar de baja productos del menú, actualizando sus precios de venta y categorías.

### B. Requisitos No Funcionales (RNF)
Los requerimientos no funcionales definen limitaciones o restricciones impuestas a los servicios o funciones que ofrece el sistema (fiabilidad, seguridad, rendimiento, usabilidad, etc.).

*   **RNF1 (Disponibilidad de Servicio):** El sistema debe garantizar una disponibilidad del **99.5%** durante el horario de atención al público del kiosco (todos los días de 08:00 a 24:00 horas).
*   **RNF2 (Tiempo de Respuesta - Rendimiento):** El tiempo necesario para procesar el registro de un pedido y enviar la comanda correspondiente a la impresora de la cocina no debe superar los **2 segundos** bajo condiciones normales de carga.
*   **RNF3 (Seguridad y Autenticación):** El acceso a las funciones administrativas críticas (arqueo de caja, reportes financieros y cambio de precios del menú) debe estar estrictamente restringido mediante autenticación de usuario únicamente para el rol de Encargado.
*   **RNF4 (Portabilidad y Compatibilidad):** La aplicación debe ser accesible a través de navegadores web estándar (Google Chrome, Mozilla Firefox y Safari) tanto desde terminales de escritorio como de dispositivos móviles (tablets y smartphones).
*   **RNF5 (Usabilidad / Capacitación):** El sistema debe poseer una interfaz táctil intuitiva diseñada de forma tal que un operador nuevo requiera un tiempo de capacitación menor a **1 hora** para registrar pedidos sin cometer más de 2 errores promedio por jornada.

---

## 4. Casos de Uso del Sistema

A partir de los requisitos iniciales, se han modelado cinco (5) casos de uso que describen escenarios completos de interacción de los actores con el sistema, detallando el flujo primario de éxito sin utilizar declaraciones condicionales complejas.

### Caso de Uso 1: Registrar Pedido
*   **Nombre del caso de uso:** Registrar Pedido
*   **Actor(es) involucrado(s):** Cajero (principal), Cliente (secundario)
*   **Descripción breve:** Permite al cajero capturar y cargar en el sistema los productos solicitados por el cliente, generando una orden de pedido activa.
*   **Flujo principal de eventos (Ruta feliz):** 
    1. El Cajero inicia el caso de uso seleccionando la opción "Registrar Pedido" en la pantalla de facturación.
    2. El sistema presenta el menú interactivo categorizado de productos disponibles.
    3. El Cajero selecciona cada uno de los productos indicados por el Cliente y especifica las cantidades.
    4. El sistema actualiza en tiempo real el detalle del pedido y calcula el monto total acumulado.
    5. El Cajero confirma el pedido, y el sistema genera un número correlativo único de orden, almacena el pedido con estado "Pendiente" e imprime el ticket de cobro para el cliente. 
*   **Precondiciones:** El Cajero debe estar autenticado en el sistema. Los productos seleccionados deben estar dados de alta en el menú del kiosco.
*   **Postcondiciones:** El pedido queda guardado de manera persistente en la base de datos con estado "Pendiente" para su correspondiente cobro.

### Caso de Uso 2: Cobrar Pedido
*   **Nombre del caso de uso:** Cobrar Pedido 
*   **Actor(es) involucrado(s):** Cajero (principal) 
*   **Descripción breve:** Registra la transacción de cobro financiero de una orden de pedido existente a través del medio de pago seleccionado.
*   **Flujo principal de eventos (Ruta feliz):** 
    1. El Cajero selecciona la opción "Cobrar Pedido" en su terminal de caja.
    2. El sistema solicita el número correlativo del pedido y el Cajero lo ingresa.
    3. El sistema busca y muestra en pantalla el detalle de los productos y el monto total de la orden.
    4. El Cajero selecciona el medio de pago (Efectivo, Tarjeta o Transferencia) ingresando el importe recibido.
    5. El Cajero confirma la transacción, y el sistema registra la entrada en caja, cambia el estado del pedido a "Pagado" e imprime el comprobante fiscal y la comanda física para la cocina.
*   **Precondiciones:** El pedido ingresado debe existir en el sistema en estado "Pendiente" de pago.
*   **Postcondiciones:** El pedido cambia a estado "Pagado", se actualiza el saldo de caja diario y se autoriza automáticamente la cola de preparación en la cocina.

### Caso de Uso 3: Preparar Pedido (Cocina)
*   **Nombre del caso de uso:** Preparar Pedido 
*   **Actor(es) involucrado(s):** Cocinero (principal) 
*   **Descripción breve:** Permite al personal de cocina ver las órdenes pagadas pendientes de preparación y cambiar el estado del pedido a medida que avanza su elaboración.
*   **Flujo principal de eventos (Ruta feliz):** 
    1. El Cocinero visualiza en el monitor del panel de la cocina la grilla de pedidos activos ordenados de forma cronológica.
    2. El Cocinero selecciona un pedido en estado "Pagado" para iniciar su preparación.
    3. El sistema cambia el estado del pedido a "En preparación" y actualiza la pantalla visible de los clientes.
    4. Tras finalizar la cocción y el armado de la orden, el Cocinero selecciona la opción "Marcar como Listo".
    5. El sistema cambia el estado del pedido a "Listo para retirar", emite una alerta sonora en el salón del kiosco y actualiza la pantalla de entrega de pedidos.
*   **Precondiciones:** El pedido seleccionado debe encontrarse en estado "Pagado".
*   **Postcondiciones:** El pedido se actualiza en el sistema a estado "Listo para retirar", liberando al cocinero para tomar la siguiente comanda pendiente [41, 42].

### Caso de Uso 4: Consultar Catálogo del Menú
*   **Nombre del caso de uso:** Consultar Catálogo del Menú 
*   **Actor(es) involucrado(s):** Cliente (principal), Cajero (secundario)
*   **Descripción breve:** Permite visualizar los productos del menú, sus precios unitarios actualizados y la disponibilidad de stock en el inventario.
*   **Flujo principal de eventos (Ruta feliz):** 
    1. El usuario selecciona la opción "Ver Menú" en la terminal de autoservicio o caja.
    2. El sistema presenta un listado de categorías (Gaseosas, Comidas rápidas, Golosinas, Combos [43, 44].
    3. El usuario selecciona una categoría específica de interés.
    4. El sistema recupera y muestra la lista de todos los productos pertenecientes a esa categoría con sus respectivos precios vigentes y fotos ilustrativas.
    5. El usuario selecciona un producto individual para visualizar su stock disponible en góndola.
*   **Precondiciones:** Los productos deben estar previamente dados de alta en el inventario activo del kiosco.
*   **Postcondiciones:** El usuario finaliza la navegación y el sistema regresa automáticamente a la pantalla de bienvenida o inicio tras 30 segundos de inactividad.

### Caso de Uso 5: Cancelar Pedido
*   **Nombre del caso de uso:** Cancelar Pedido
*   **Actor(es) involucrado(s):** Cajero (principal), Encargado (secundario) 
*   **Descripción breve:** Permite anular de forma permanente un pedido registrado en el sistema que aún no haya sido retirado por el cliente, registrando la causa y requiriendo aprobación del encargado.
*   **Flujo principal de eventos (Ruta feliz):** 
    1. El Cajero selecciona la opción "Cancelar Pedido" e ingresa el número correlativo del pedido a anular.
    2. El sistema muestra en pantalla el detalle del pedido activo para su verificación.
    3. El Cajero selecciona el motivo de la cancelación de una lista predefinida en pantalla.
    4. El sistema solicita la clave de autorización administrativa del Encargado.
    5. El Encargado ingresa su clave de supervisor, y el sistema aprueba la anulación, cambia el estado del pedido a "Cancelado" y restituye los productos e ingredientes al stock del inventario.
*   **Precondiciones:** El pedido a cancelar debe existir en el sistema y encontrarse en estado "Pendiente", "Pagado" o "En preparación" (no puede estar en estado "Entregado").
*   **Postcondiciones:** El pedido queda registrado con estado histórico "Cancelado" y se registra la anulación y la devolución de stock correspondiente.
