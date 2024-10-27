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

**Ejercicios CREATE**

```sql
-- 1. Inserta 5 productos diferentes en la tabla `productos`.
INSERT INTO productos (nombre, categoria, precio, stock)
VALUES
('Bálsamo de Jinjia', 'Cuidado Personal', 50.00, 30),
('Infusión de Salvia', 'Bebidas', 20.00, 15),
('Camisa de Lino Alberic', 'Ropa', 120.00, 50),
('Cuaderno de Solomia', 'Papelería', 8.50, 100),
('Aceite de Tamarín', 'Cuidado Personal', 75.00, 0);
-- Cada inserción representa un producto con categoría, precio y stock inicial.

-- 2. Registra 3 clientes en la tabla `clientes`.
INSERT INTO clientes (nombre, correo)
VALUES
('Teodoro Pacheco', 'teodoro.pacheco@example.com'),
('Zenobia Larios', 'zenobia.larios@example.com'),
('Artemisa Becerra', 'artemisa.becerra@example.com');
-- Se registran tres clientes con nombres únicos y correos electrónicos diferentes.

-- 3. Inserta 2 pedidos hechos por diferentes clientes.
-- Pedido de Teodoro Pacheco con 2 productos
INSERT INTO pedidos (cliente_id, total)
VALUES (1, 100.00);

INSERT INTO detalle_pedidos (pedido_id, producto_id, cantidad, precio_unitario)
VALUES
(1, 1, 2, 50.00),
(1, 2, 1, 20.00);

-- Pedido de Zenobia Larios con 2 productos
INSERT INTO pedidos (cliente_id, total)
VALUES (2, 240.00);

INSERT INTO detalle_pedidos (pedido_id, producto_id, cantidad, precio_unitario)
VALUES
(2, 3, 1, 120.00),
(2, 4, 5, 8.00);
-- Cada pedido tiene al menos dos productos con sus cantidades y precios.
```
