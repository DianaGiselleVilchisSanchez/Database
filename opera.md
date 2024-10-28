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
**Ejercicios DELETE**
```sql
-- 1. Elimina todos los productos de la tabla `productos` que no tienen stock disponible.
DELETE FROM productos
WHERE stock = 0;
-- Borra productos cuyo stock es 0, es decir, los que no tienen inventario disponible.

-- 2. Borra un pedido que fue cancelado por el cliente.
DELETE FROM detalle_pedidos
WHERE pedido_id = 1;

DELETE FROM pedidos
WHERE pedido_id = 1;
-- Elimina el pedido con ID 1 y sus detalles en `detalle_pedidos` de la tabla `pedidos`.

-- 3. Elimina un cliente que ha solicitado la eliminación de su cuenta.
DELETE FROM pedidos
WHERE cliente_id = 3;

DELETE FROM clientes
WHERE cliente_id = 3;
-- Primero elimina los pedidos relacionados al cliente con ID 3 y luego elimina al cliente.
```