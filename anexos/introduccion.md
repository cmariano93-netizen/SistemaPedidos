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
