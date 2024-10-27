**Creación de la base de datos y tablas**
```sql
CREATE DATABASE tienda_virtual;

USE tienda_virtual;

CREATE TABLE productos (
    producto_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    categoria VARCHAR(50),
    precio DECIMAL(10, 2),
    stock INT,
    fecha_creacion DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE clientes (
    cliente_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) UNIQUE,
    fecha_registro DATE DEFAULT CURDATE()
);

CREATE TABLE pedidos (
    pedido_id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT,
    fecha_pedido DATETIME DEFAULT CURRENT_TIMESTAMP,
    total DECIMAL(10, 2),
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id)
    ON UPDATE CASCADE ON DELETE RESTRICT
);

CREATE TABLE detalle_pedidos (
    detalle_id INT AUTO_INCREMENT PRIMARY KEY,
    pedido_id INT,
    producto_id INT,
    cantidad INT,
    precio_unitario DECIMAL(10, 2),
    FOREIGN KEY (pedido_id) REFERENCES pedidos(pedido_id)
    ON UPDATE CASCADE ON DELETE RESTRICT,
    FOREIGN KEY (producto_id) REFERENCES productos(producto_id)
    ON UPDATE CASCADE ON DELETE RESTRICT
);
```

**Ejercicios READ**

```sql
-- 1. Obtén una lista de todos los productos que tienen un stock mayor a 10 unidades.
SELECT producto_id, nombre, precio, stock
FROM productos
WHERE stock > 10;
-- Muestra productos con stock mayor a 10, incluyendo su ID, nombre, precio y stock.

-- 2. Encuentra los pedidos realizados por un cliente en particular (Zenobia Larios).
SELECT clientes.nombre, pedidos.pedido_id, pedidos.fecha_pedido, pedidos.total
FROM clientes
JOIN pedidos ON clientes.cliente_id = pedidos.cliente_id
WHERE clientes.nombre = 'Zenobia Larios';
-- Muestra pedidos de Zenobia Larios, con nombre del cliente, ID de pedido, fecha y total.

-- 3. Muestra el total de ventas por cada producto.
SELECT productos.nombre, SUM(detalle_pedidos.cantidad) AS total_vendido
FROM productos
JOIN detalle_pedidos ON productos.producto_id = detalle_pedidos.producto_id
GROUP BY productos.producto_id;
-- Agrupa los productos por su ID y muestra el nombre y cantidad total vendida.
```
