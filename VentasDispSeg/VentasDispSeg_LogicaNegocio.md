# Ventas

## Listado de Entidades

### ventas **(ED)**
- venta_id **PK**
- fecha_solicitud
- fecha_ejecucion
- cliente_id **FK**
- vendedor_id **FK**
- domicilio_facturacion_id **FK**
- domicilio_instalacion_id **FK**
- orden
- medio_depago_id **FK**
- base_imponible
- impuestos
- descuento
- total

### clientes **(ED)**
- cliente_id **PK**
- nombre_o_razonsocial
- apellidos
- estado_cliente_id **FK**
- clasificacion_persona_id **FK**
- cuit_cuil **UQ**
- detalle_iva_id **FK**
- detalle_iibb_id **FK**
- celular_telefono **UQ**
- correo **UQ**
- alto_riesgo
- mascotas
- tiempo_actividad

### estado_cliente **(EC)**
- estado_cliente_id **PK**
- condicion

### clasificaciones_persona **(EC)**
- clasificacion_persona_id **PK**
- tipo


### detalles_iva **(EC)**
- detalle_iva_id **PK**
- condicion


### detalles_iibb **(EC)**
- detalle_iibb_id **PK**
- condicion

### domicilios_de_facturacion **(EP)**
- domicilio_facturacion_id **PK**
- direccion_id **FK**

### domicilios_de_instalacion **(EP)**
- domicilio_instalacion_id **PK**
- direccion_id **FK**

### direcciones **(ED)**
- direccion_id **PK**
- cliente_id **FK**
- calle
- numero
- piso
- depto
- cpa
- localidad
- povincia
- dominio_pais **FK**

### paises **(EC)**
- dominio_pais **PK**
- nombre

### vendedores **(ED)** <Se considera entidad de datos ya que en cualquier momento un vendedor puede dejar la empresa> 
- vendedor_id **PK**
- nombres
- apellidos
- legajo **UQ**

### pedidos **(EP)**
- pedido_id **PK**
- venta_id **FK**
- producto_id **FK**
- cantidad

### productos **(ED)** <Se considera entidad de datos ya que el stock disponible cambia o bien pueden ingresar nuevos productos entre otras posibilidades>
- producto_id **PK**
- nombre
- cant_stock
- precio_unitario

### medios_de_pago **(EC)**
- medio_depago_id **PK**
- opciones

## Relaciones

1. Un **cliente** genera una **venta** (_1 a M_).
1. Un **cliente** tiene un **estado_cliente** (_1 a 1_).
1. Un **cliente** se categoriza por **clasificacion_persona** (_1 a 1_).
1. Un **cliente** tiene **detalle_iva** (_1 a 1_).
1. Un **cliente** tiene **detalle_iibb** (_1 a 1_).
1. Un **cliente** registra una **direccion** (_1 a M_).
1. Un **cliente** genera una **venta** (_1 a M_).
1. Un **vendedor** gestiona una **venta** (_1 a M_).
1. Una **venta** refiere a un **domicilio_facturacion** (_1 a 1_).
1. Una **venta** refiere a un **domicilio_instalacion** (_1 a 1_).
1. Una **venta** ofrece un **medio_depago** (_1 a 1_).
1. Una **venta** tiene un **pedido** (_1 a M_).
1. Un **pedido** abarca un **producto** (_1 a M_).
1. Un **domicilio_facturacion** corresponde a una **direccion** (_1 a 1_).
1. Un **domicilio_instalacion** corresponde a una **direccion** (_1 a 1_).
1. Una **direccion** corresponde a una **provincia** (_1 a 1_).
1. Una **direccion** corresponde a un **pais** (_1 a 1_).

## Diagrama

### Modelo Entidad - Relación

![Modelo Entidad - Relación](./MR-VentasDispSeg(v3).png)

## Reglas de negocio

### ventas
1. Crear una venta.
1. Leer todas las ventas.
1. Leer una venta en particular.
1. Leer todas las ventas de un cliente.
1. Leer todas las ventas de un producto.
1. Actualizar una venta.
1. Eliminar una venta
<Observese que esta ultima opcion debe ser tratada con sumo detalle ya que si bien se puede eliminar el registro de una venta por normativa la orden emitida al efectuarse la operacion conlleva un smart contract dejando su respectivo hash por lo tanto la operacion seguira figurando en la plataforma blockchain que usa la empresa>

### clientes

1. Crear un cliente.
1. Leer todos los clientes.
1. Leer un cliente en particular.
1. Actualizar un cliente.
1. Eliminar un cliente.

### direcciones

1. Crear una dirección.
1. Leer todas las direcciones.
1. Leer una dirección en particular.
1. Actualizar una dirección.
1. Eliminar una dirección.

### provincias

1. Crear una provincia.
1. Leer todas las provincias.
1. Leer una provincia en particular.
1. Actualizar una provincia.
1. Eliminar una provincia.

### paises

1. Crear un país.
1. Leer todos los países.
1. Leer un país en particular.
1. Actualizar un país.
1. Eliminar un país.


### vendedores

1. Crear un vendedor.
1. Leer todos los vendedores.
1. Leer un vendedor en particular.
1. Actualizar un vendedor.
1. Eliminar un vendedor.

### pedidos

1. Crear un pedido.
1. Leer todos los pedidos.
1. Leer un pedido en particular.
1. Leer todos los pedidos de una venta.
1. Leer todos los pedidos de una producto.
1. Leer todos los pedidos de una cliente.
1. Actualizar un pedido.
1. Eliminar un pedido.


### productos

1. Crear un producto.
1. Leer todos los productos.
1. Leer un producto en particular.
1. Actualizar un producto.
1. Eliminar un producto.
1. Restar el número de articulos solicitados a la cantidad de productos disponibles según corresponda.
