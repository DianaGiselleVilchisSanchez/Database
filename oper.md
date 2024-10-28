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

**Ejercicios UPDATE**
```sql

-- 1. Actualiza el precio de todos los productos de la categoría 'Cuidado Personal' aumentando un 15%.
UPDATE productos
SET precio = precio * 1.15
WHERE categoria = 'Cuidado Personal';
-- Incrementa el precio de productos en la categoría 'Cuidado Personal' en un 15%.

-- 2. Modifica el correo de uno de los clientes por un nuevo correo electrónico.
UPDATE clientes
SET correo = 'nuevo.teodoro@example.com'
WHERE nombre = 'Teodoro Pacheco';
-- Actualiza el correo del cliente 'Teodoro Pacheco' por uno nuevo y único.

-- 3. Corrige el stock de un producto cuyo stock actual es incorrecto.
UPDATE productos
SET stock = 20
WHERE producto_id = 5;
-- Actualiza el stock del producto con ID 5 (Aceite de Tamarín) a 20.
```
