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












### Requisitos funcionales

*RF1 - Registrar pedido*  
El sistema debe permitir registrar un pedido con sus productos, cantidades y personalizaciones.

*RF2 - Identificar pedido para retiro*  
El sistema debe permitir identificar cada pedido mediante un número de pedido y un nombre o referencia de retiro.

*RF3 - Calcular total del pedido*  
El sistema debe calcular el total del pedido teniendo en cuenta los productos, cantidades y personalizaciones.

*RF4 - Registrar pago*  
El sistema debe permitir registrar el pago de un pedido y su forma de pago.

*RF5 - Enviar pedido a cocina*  
El sistema debe enviar automáticamente el pedido a cocina una vez registrado.

*RF6 - Consultar pedidos activos*  
El sistema debe permitir visualizar los pedidos activos y su estado actual.

*RF7 - Cambiar estado del pedido*  
El sistema debe permitir cambiar el estado de un pedido entre recibido, en preparación, listo y entregado.

*RF8 - Cancelar pedido*  
El sistema debe permitir cancelar un pedido completo cuando las reglas del estado del pedido lo permitan.

*RF9 - Marcar pedido como prioritario*  
El sistema debe permitir marcar manualmente un pedido como prioritario.

*RF10 - Modificar pedido*  
El sistema debe permitir modificar un pedido mientras se encuentre en estado recibido.

*RF11 - Agregar o quitar productos*  
El sistema debe permitir agregar o quitar productos de un pedido mientras se encuentre en estado recibido.

*RF12 - Modificar personalizaciones*  
El sistema debe permitir agregar, quitar o modificar las personalizaciones de los productos de un pedido mientras se encuentre en estado recibido.

*RF13 - Registrar entrega del pedido*  
El sistema debe permitir registrar que un pedido listo fue entregado al cliente.

### Estados del pedido

- recibido: permitir modificar, agregar/quitar productos, cancelar y priorizar.
- en preparación: permitir priorizar y consultar; bloquear modificaciones.
- listo: permitir registrar entrega; bloquear modificaciones.
- entregado: solo consulta.
- cancelado: solo consulta histórica y no aparece en la lista de pedidos activos.

### Requisitos no funcionales

*RNF1 - Información actualizada*  
El sistema debe mantener la información de los pedidos actualizada para que el personal pueda consultar el mismo estado y la misma información del pedido.

*RNF2 - Consistencia de la información*  
El sistema debe evitar que se pierda o se duplique la información de los pedidos.

*RNF3 - Facilidad de uso*  
El sistema debe ser sencillo de utilizar para el personal del kiosco, permitiendo consultar y actualizar la información de los pedidos de forma clara.

*RNF4 - Integridad de los pedidos*  
El sistema debe conservar la información de los pedidos, incluso cuando un pedido sea cancelado, sin eliminarlo del sistema.

*RNF5 - Rendimiento y velocidad de sincronización*  
El sistema debe actualizar el estado de un pedido entre mostrador y cocina en un máximo de 3 segundos, con una tasa de sincronización del 95% de los eventos dentro de ese umbral.











---
***CASOS DE USO***
- Nombre del caso de uso: Registrar pedido.
    - Actor principal: Personal de atención.
    - Descripción breve: El personal que atiende a los clientes debe registrar las comandas y entregarlas una vez listas o elaboradas.
    - Flujo principal de eventos:  
        - Actor: Ingresa al sistema y selecciona una mesa disponible.
        - Sistema: Muestra listas de productos.
        - Actor: Selecciona las comandas.
        - Sistema:  Envía la lista de comandas a cocina/mostrador donde corresponda.
        - Actor: Confirma el pedido en el sistema.
        - Sistema: Genera registro de las comandas y calcula costos.
    - Precondiciones: La mesa debe estar disponible y no debe tener consumos registrados previamente.
    - Postcondiciones: Se instanció un nuevo objeto "Pedido" con estado de solicitado, asociado a una mesa seleccionada y el área de preparación fue notificado.
- Nombre del caso de uso: Cobrar cuenta.
    - Actor principal: Cobrador.
    - Descripción breve: El cobrador debe ofrecer los medios de pago, imprimir ticket de cuenta, realizar el cobro.
    - Flujo principal de eventos:  
        - Actor: Cierra la mesa.
        - Sistema: Listar el ticket de detalles y procesar el total de la cuenta.
        - Actor: Imprimir ticket y confirma el cobro.
        - Sistema: Registra la venta.
        - Actor: Actualiza el estado de la mesa y registra el cobro.
    - Precondiciones: La mesa debe estar en estado de abierta/ocupada y tener consumos registrados.
    - Postcondiciones: Se actualizó el estado de la mesa a cerrada o disponible y el pedido pasa a estado de cobrado.
- Nombre del caso de uso: Cancelar comanda.
    - Actor principal: Personal  de atención.
    - Descripción breve: El actor debe poder cancelar una comanda si el estado esta en la instancia de proceso.
    - Flujo principal de eventos:
        - Actor: Observa el estado de la comanda.
        - Sistema: En función del estado de preparación Solicitado, En Proceso, listo. Si se encuentra en solicitado o en proceso habilita cancelar comanda.
        - Actor: Confirma la cancelación.
        - Sistema: Borra del carrito la comanda.
        - Actor: Actualiza los cambios.
    - precondiciones: El estado de la comanda debe estar en solicitado o en proceso.
    - Postcondiciones: El objeto "comanda" cambia su atributo a estado "cancelado", se eliminan los productos del carrito de la mesa y se recalculan los costos acumulados .
- Nombre del caso de uso: Preparar pedido.
    - Actor principal: Cocinero.
    - Descripción breve: El área de cocina debe recibir la instrucción de los pedidos y los prepara.
    - Flujo principal de eventos: 
        - Actor: Recibe notificación de comanda, establece el cambio “solicitado" → 
        "en proceso".
        - Sistema: Sincroniza el estado de las comandas.
        - Actor: Acciona la casilla de verificación de listo para retirar.
        - Sistema: Notifica que las comandas están listas para retirar en cocina.
        - Actor: Realiza la confirmación de comanda entregada.
    - Precondiciones: El estado de la comanda debe estar en solicitado.
    - Postcondiciones: El objeto "pedido" paso a estado "listo para retirar", y el sistema envia una notificación.
- Nombre del caso de uso: Priorizar pedido.
    - Actor principal: Supervisor.
    - Descripción breve: Las personas asignadas pueden indicar prioridad en la preparación de pedidos.
    - Flujo principal de eventos: 
        - Actor: Selecciona un pedido activo en preparación desde el tablero de control.
        - Sistema: Muestra las opciones de gestión del pedido.
        - Actor: Selecciona "Fijar Prioridad Alta".
        - Sistema: Modifica el atributo de prioridad y resalta el pedido en el tablero de cocina de manera visual.
        - Actor: Confirma la operación.
    - Precondiciones: El objeto "pedido" ya debe existir en el sistema en estado de solicitado.
    - Postcondiciones: Se agregó prioridad al pedido y se notificó al área de preparación.

