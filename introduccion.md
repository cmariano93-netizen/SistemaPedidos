# Requisitos iniciales del sistema
### Cuaderno de análisis
NotebookLM: https://notebook.google.com/notebook/4dab293b-0441-4235-a64d-10e886ddbb70
### RF1 - Registrar pedido
El sistema debe permitir registrar un pedido con sus productos, cantidades y personalizaciones.

### RF2 - Identificar pedido para retiro
El sistema debe permitir identificar cada pedido mediante un número de pedido y un nombre o referencia de retiro.

### RF3 - Calcular total del pedido
El sistema debe calcular el total del pedido teniendo en cuenta los productos, cantidades y personalizaciones.

### RF4 - Registrar pago
El sistema debe permitir registrar el pago de un pedido y su forma de pago.

### RF5 - Enviar pedido a cocina
El sistema debe enviar automáticamente el pedido a cocina una vez registrado.

### RF6 - Consultar pedidos activos
El sistema debe permitir visualizar los pedidos activos y su estado actual.

### RF7 - Cambiar estado del pedido
El sistema debe permitir cambiar el estado de un pedido entre recibido, en preparación, listo y entregado.

### RF8 - Cancelar pedido
El sistema debe permitir cancelar un pedido completo cuando las reglas del estado del pedido lo permitan.

### RF9 - Marcar pedido como prioritario
El sistema debe permitir marcar manualmente un pedido como prioritario.

### RF10 - Modificar pedido
El sistema debe permitir modificar un pedido mientras se encuentre en estado recibido.

### RF11 - Agregar o quitar productos
El sistema debe permitir agregar o quitar productos de un pedido mientras se encuentre en estado recibido.

### RF12 - Modificar personalizaciones
El sistema debe permitir agregar, quitar o modificar las personalizaciones de los productos de un pedido mientras se encuentre en estado recibido.

### RF13 - Registrar entrega del pedido
El sistema debe permitir registrar que un pedido listo fue entregado al cliente.
## Requisitos no funcionales 
### RNF1 - Información actualizada
El sistema debe mantener la información de los pedidos actualizada para que el personal pueda consultar el mismo estado y la misma información del pedido.

### RNF2 - Consistencia de la información
El sistema debe evitar que se pierda o se duplique la información de los pedidos.

### RNF3 - Facilidad de uso
El sistema debe ser sencillo de utilizar para el personal del kiosco, permitiendo consultar y actualizar la información de los pedidos de forma clara.

### RNF4 - Integridad de los pedidos
El sistema debe conservar la información de los pedidos, incluso cuando un pedido sea cancelado, sin eliminarlo del sistema.

