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
- subtotal
- total

### clientes **(ED)**
- cliente_id **PK**
- nombre_o_razonsocial
- apellidos
- estado_cliente_id **FK**
- clasificacion_persona_id **FK**
- cuit_cuil
- detalle_iva_id **FK**
- detalle_iibb_id **FK**
- celular_telefono
- correo
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

### domicilios_de_facturacion **(ED)**
- domicilio_facturacion_id **PK**
- direccion_id **FK**

### domicilios_de_instalacion **(ED)**
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

### vendedores **(ED)** <> Se considera entidad de datos ya que en cualquier momento un vendedor puede dejar la empresa.
- vendedor_id **PK**
- nombres
- apellidos
- legajo **FK**

### pedidos **(ED)**
- pedido_id **PK**
- venta_id **FK**
- producto_id **FK**
- cantidad

### productos **(ED)** <> Se considera entidad de datos ya que el stock disponible varía, o bien pueden ingresar nuevos productos, entre otras posibilidades.
- producto_id **PK**
- nombre
- cant_stock
- precio_unitario

### medios_de_pago **(EC)**
- medio_depago_id **PK**
- opciones