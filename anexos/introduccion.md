# Anexo I: Introducción al Diseño Orientado a Objetos e Ingeniería de Requerimientos

---

## 1. Descripción del Paradigma Orientado a Objetos

El **Paradigma Orientado a Objetos (POO)** representa una evolución crítica en la ingeniería de software que supera de forma práctica las limitaciones estructurales del enfoque tradicional o "procedimental". Mientras que la programación estructurada se centra de manera lineal en la pregunta *¿qué hace este programa?* y divide el software en funciones y procedimientos independientes, el modelo orientado a objetos responde a la interrogante: ***¿qué objetos del mundo real se pueden modelar?***

Este paradigma organiza el software estructurando el sistema en torno a **objetos lógicos interactivos** que combinan y encapsulan tanto los datos (atributos) como los comportamientos que operan directamente sobre ellos (métodos). La importancia de adoptar la POO en el desarrollo del **"SistemaPedidos"** radica en sus tres grandes beneficios arquitectónicos:
1.  **Modularidad:** Permite segmentar el sistema en componentes independientes y altamente cohesivos.
2.  **Mantenibilidad:** Al encapsular el estado y el código dentro de un objeto, cualquier modificación posterior tiene un impacto mínimo en otros módulos del sistema, reduciendo drásticamente el costo de mantenimiento a largo plazo.
3.  **Reutilización (Reusabilidad):** Permite diseñar plantillas lógicas (clases) para definir propiedades comunes y usarlas de manera repetitiva en distintas partes de la aplicación sin necesidad de reescribir código desde el principio.

---

## 2. Los Cuatro Fundamentos de POO (Aplicados al Kiosco "Sabor")

Para sentar las bases de la arquitectura lógica del **SistemaPedidos**, aplicamos de manera conceptual los cuatro principios fundamentales de la POO sobre el dominio del negocio [7]:

### 🚀 A. Abstracción
*   **Definición:** Consiste en reducir la complejidad del mundo real descartando los detalles técnicos o circunstanciales que no son de interés, para modelar únicamente los aspectos esenciales y relevantes para el contexto específico del sistema.
*   **Aplicación en el Kiosco:** Al diseñar la clase **`Producto`**, identificamos de manera abstracta las propiedades indispensables para el proceso comercial de ventas en el salón y la cocina: su identificador (`idProducto`), su nombre comercial (`nombre`), su valor al público (`precioUnitario`) y su disponibilidad en depósito (`stockDisponible`). Ignoramos por completo detalles complejos de la realidad que no aportan valor a este entregable, como las dimensiones físicas del embalaje del producto, el costo de logística de distribución del proveedor o el sistema de refrigeración requerido para su conservación [12, 15].

### 🛡️ B. Encapsulación
*   **Definición:** Es el proceso de empaquetar de forma hermética los datos y los comportamientos en una sola unidad (la clase), ocultando la implementación interna del objeto al mundo exterior y exponiendo únicamente una interfaz pública y controlada de comunicación.
*   **Aplicación en el Kiosco:** En la clase **`Pedido`**, definimos el atributo `montoTotal` con visibilidad **privada (`-`)** para protegerlo de manipulaciones externas accidentales o no autorizadas. Ninguna clase externa puede modificar de forma directa este saldo monetario [16]. El objeto resguarda su estado interno exponiendo el método **público (`+`)** `agregarProducto(Producto, cantidad)`, el cual se encarga de disparar internamente la operación de actualización del monto de manera segura y regulada.

### 🌳 C. Herencia
*   **Definición:** Es un mecanismo de relación jerárquica que permite que una clase secundaria (clase derivada o hija) adquiera de manera automática e implícita todas las propiedades (atributos) y comportamientos (métodos) de una clase primaria (clase base o madre), posibilitando la extensión o especialización de su comportamiento lógico.
*   **Aplicación en el Kiosco:** El sistema del kiosco maneja personas con credenciales de acceso. Podemos diseñar una clase general y abstracta llamada **`Usuario`** que contenga los atributos comunes `- idUsuario`, `- nombre`, `- email` y `- contrasenia`, junto con el método público `+ iniciarSesion()` [22-24]. Mediante la herencia, creamos las clases derivadas **`Empleado`** y **`Cliente`**. Ambas clases hijas heredan implícitamente todo el comportamiento de la clase base sin necesidad de programar nuevamente la validación de inicio de sesión, permitiendo que `Empleado` se especialice agregando su atributo único `- salario`.

### 🎭 D. Polimorfismo
*   **Definición:** Es la capacidad de que objetos de distintas clases pertenecientes a una misma jerarquía respondan de maneras diferentes e individuales ante la recepción de un mismo mensaje o llamada a método.
*   **Aplicación en el Kiosco:** Imaginemos una superclase abstracta de comportamiento llamada **`Pago`** con un método público `procesarCobro()`. De ella heredan las subclases concretas **`PagoEfectivo`** y **`PagoTransferencia`**. Cuando el sistema invoca de forma genérica el mensaje `procesarCobro()` sobre el pago de una orden, el objeto `PagoEfectivo` responderá registrando el ingreso en la caja física y abriendo el cajón, mientras que el objeto `PagoTransferencia` responderá disparando una llamada de validación electrónica hacia la API bancaria externa. Esto otorga una enorme flexibilidad y extensibilidad para añadir nuevos medios de pago en el futuro sin alterar la lógica de cobro general.


























---

### CASOS DE USO

---
- **Nombre del caso de uso**: Levantar pedido.
    - Actor principal: Mozo / Cajero-Mostrador / Encargada de turno.
    - Descripcion breve: El personal que atiende a los clientes debe registrar las comandas y entregarlas una vez listas o elaboradas.
    - Flujo principal de eventos:  
        - Actor: Ingresa al sistema y registra una mesas.
        - Sistema: Ofrece el menu desplegable de opcines para completar comanda.
        - Actor: Selecciona las comandas, accion de confirmar.
        - Sistema: Al confirmar el menu, desplega la accion siguiente a cocina/mostrador donde corresponda y vuelve a mostrar el menu desplegable de toma de pedidos de la mesa.
        - Actor: registra las entregas de la mesa en el sistema y confirma.
        - Sistema: Actualiza los estados de entrega y vuelve a mostrar menu desplegable de toma de pedidos de la mesa.
    - Precondiciones: El actor debe estar logeado con su usario y contraseña.
    - Postcondiciones: Se genero solicitud de comandas con exito.
- **Nombre del caso de uso**: Cobrar la cuenta.
    - Actor principal: Mozo / Cajero-Mostrador / Encargada de turno.
    - Descripcion breve: El cobrador debe ofrecer los medios de pago, imprimir ticket de cuenta, realizar el cobro.
    - Flujo principal de eventos:  
        - Actor: Pasar el estado de la mesa a cerrada.
        - Sistema: Listar el ticket de detalles y procesar el total de la cuenta.
        - Actor: Imprimir ticket.
        - Sistema: Ofrecer menu de cobro recepcionado.
        - Actor: Confirmar cobro.
        - Sistema: Mostrar menu general de mesas.
    - Precondiciones: El actor debe estar logeado con su usario y contraseña.
    - Postcondiciones: Se confirmo y registro el pago.
- **Nombre del caso de uso**: Cancelar pedido.
    - Actor principal: Mozo / Cajero-Mostrador / Encargada de turno.
    - Descripcion breve: El actor debe poder cancelar un pedido si el estado esta en la instancia de proceso.
    - Flujo principal de eventos:
        - Actor: Se desplega al menu de la mesa y observa el estado del pedido.
        - Sistema: Informa el estado del pedido. Solicitado, En Proceso, listo. Si se encuentra en Solicitado o en proceso ofrece comando para cancelar pedido.
        - Actor: Confirma la cancelacion.
        - Sistema: Ejecuta la cancelacion del pedido. Borra del carrito el producto y vuelve a visualisar el menu desplegable de tomas de pedidos de la mesa.
        - Actor: Actualiza el historial de la mesa para que desaparescan los cambios.
    - precondiciones: El actor debe estar logeado con su usario y contraseña.
    - Postcondiciones: Se genero registro de cancelacion de pedido.
- **Nombre del caso de uso**: Elaboracion la comida.
    - Actor principal: Cocinero.
    - Descripcion breve: El area de cocina debe recibir la instruccion de los pedidos y los prepara.
    - Flujo principal de eventos: 
        - Actor: Recibe el llamado en el sistema, visualiza la mesa, evalua los pedidos y realiza confirmacion para que el estado corra de solicitado a en preparacion.
        - Sistema: Muestra solo las opciones de las comandas correspondientes a cocina, colabora con la imagen de visualizacion de la lista como ayuda de memoria.
        - Actor: Una vez terminados los platos se tilda la casilla de verificacion de listo para retirar.
        - Sistema: Realiza la solicitud de plato listo para retirar en cocina.
        - Actor: Realiza la confirmacion de plato entregado una vez que se lo llevan.
    - Precondiciones: El actor debe estar logeado con su usario y contraseña.
    - Postcondiciones: Se genero registro de entregas de cocina.
- **Nombre del caso de uso**: Solicitud de pedido prioritario.
    - Actor principal: Dueño / Encargada de turno.
    - Descripcion breve: Las personas asignadas pueden indicar prioridad en la preparacion de pedidos para llevar.
    - Flujo principal de eventos: 
        - Actor: Entra el menu desplegable de pedidos para llevar.
        - Sistema: Ofrece el menu desplegable de opcines para completar comanda.
        - Actor:   Actor: Selecciona las comandas, accion de confirmar.
        - Sistema: Al confirmar el menu, desplega la accion siguiente a cocina/mostrador donde corresponda y vuelve a mostrar el menu desplegable de toma de pedidos de las mesas.
        - Actor: Si es necesario realiza la confirmacion de pedido listo para retirar cerrada.
    - Precondiciones: El actor debe estar logeado con su usario y contraseña y cumplir con el nivel de acceso requerido.
    - Postcondiciones: Se genero registro de entregas de cocina.