# Anexo - Introducción al Diseño Orientado a Objetos

## 📝 1. Paradigma Orientado a Objetos
*Es un concepto que se usa para referirse a una forma de crear software, mediante uno o más lenguajes de programacián específicos (por ejemplo, C++ o Java).*

 *La Programación Orientada a Objetos busca estructurar el programa dividiéndolo en modelos de objetos reales o simulados que interactúan directamente entre sí.*


Las ventajas e importancia de este paradigma se basa en:
1. 🛡️ *Robustez y Seguridad del Sistema*

    Se logra mediante encapsulación y ocultación de datos internos de los objetos.
    Para leer o modificar estos datos, se hace mediante una interfaz pública invocando métodos o funciones miembro, logrando que ninguna funcion ajena al sistema pueda modificar o alterar los datos.


2. 🔧 *Mantenibilidad a Largo Plazo*

    Es la facilidad en el tiempo para corregir errores, realizar mejoras o adaptar el software sin alterar su funcionamiento general.


3. 📈 *Adaptabilidad y Extensibilidad en el Tiempo*

    Los requisitos de un negocio son dinámicos y cambian de forma inevitable. La POO aborda esta realidad permitiendo que el software evolucione con facilidad.
---

## ⚙️ 2. Los Cuatro Fundamentos de POO
*Explicar detalladamente el significado técnico de cada pilar e ilustrarlo de forma pragmática con analogías lógicas del negocio del Kiosco "Sabor" (sin necesidad de codificar en esta etapa):*

1. **Abstracción:** 
Proceso para reducir la complejidad del mundo real, enfocandose sólo en puntos relevantes y significativos para el sistema.

En SistemaPedidos un ejemplo puede ser un alfajor, que tiene diferentes propiedades (peso, tamaño, color, gusto, etc...).
Para el sistema lo importantes es la venta y facturacion del mismo.

Atributos esenciales: codigo, descripcion y precioBase.

Métodos esenciales: obtenerPrecio()


2. **Encapsulamiento:** 
Consiste en agrupar los atributos de los datos con las funciones o métodos que actúan sobre los mismos.

En SistemaPedidos un ejemplo es el valor total de un pedido(montoTotal). Este valor númerico no debe ser manipulado.
Solo puede modificarse en caso de agregar o quitar productos dentro del mismo pedido. 


3. **Herencia:** 
 Es el mecanismo estructural que permite organizar las clases en jerarquías
 
  Una clase derivada (hija) hereda y adquiere de forma automática todos los atributos y comportamientos (métodos) de una clase base (madre o superclase), posibilitando la reutilización del diseño y la extensión de comportamientos especializados sin necesidad de duplicar código.

  Aplicación práctica en el Kiosco "Sabor": 
  En el kiosco existen productos que requieren manipulación (productos elaborados como un sándwich) y productos comerciales directos (envasados como una gaseosa).
  En lugar de diseñar dos clases independientes duplicando campos, creamos la superclase genérica Producto y hacemos que dos subclases específicas hereden de ella :

  ProductoEnvasado hereda codigo y descripcion, y añade su propio atributo específico: fechaVencimiento

  ProductoElaborado hereda codigo y descripcion, y añade su propio atributo especializado de cocina: tiempoPreparacion


4. **Polimorfismo:**

 Es la capacidad que poseen diferentes objetos pertenecientes a una misma jerarquía de clases para responder de manera distinta y personalizada a un mismo mensaje o llamada de método común.

Un ejemplo en SistemaPedidos:

Si queremos calcular el precio final de un productos envasado (gaseosa), ya lo tenemos configurado.

Si queremos calcular el precio final de un producto elaborado (sándwich), se suman varios factores más, como el precio del ingrediente, precio del empaque, el precio del tiempo de preparación.












ACA AGREGAR LOS REQUISITOS FUNCIONALES Y NO FUNCIONALES











---
# ***CASOS DE USO***
- Nombre del caso de uso: Levantar pedido.
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
- Nombre del caso de uso: Cobrar la cuenta.
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
- Nombre del caso de uso: Cancelar pedido.
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
- Nombre del caso de uso: Elaboracion la comida.
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
- Nombre del caso de uso: Solicitud de pedido prioritario.
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