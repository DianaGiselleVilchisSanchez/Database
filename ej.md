**Ejercicios CREATE**
```sql
-- 1. Inserta un cliente válido en la tabla.
INSERT INTO clientes (nombre, email, telefono, direccion)
VALUES ('Roberto Martínez', 'roberto.martinez@example.com', '5558765432', 'Calle Luna 15');
-- 2. Inserta un cliente sin especificar el campo id_cliente.
INSERT INTO clientes (nombre, email, telefono, direccion)
VALUES ('Lucía Fernández', 'lucia.fernandez@example.com', '5556543219', 'Av. Sol 29');


-- 3. Intenta insertar un cliente con un formato de correo incorrecto (debería fallar).
INSERT INTO clientes (nombre, email, telefono, direccion)
VALUES ('Pedro González', 'pedro.gonzalezexample.com', '5559123456', 'Paseo de la Luna 50');


-- 4. Inserta múltiples clientes en una sola consulta.
INSERT INTO clientes (nombre, email, telefono, direccion)
VALUES
('Ana Torres', 'ana.torres@example.com', '5553216789', 'Calle del Sol 2'),
('José Ramírez', 'jose.ramirez@example.com', '5552138765', 'Av. de la Paz 45');


-- 5. Inserta un cliente con un número de teléfono de menos de 10 caracteres (debería fallar).
INSERT INTO clientes (nombre, email, telefono, direccion)
VALUES ('María Gutiérrez', 'maria.gutierrez@example.com', '12345', 'Plaza Mayor 9');
```


**Ejercicios READ**
```sql
-- 1. Consulta todos los registros de la tabla `clientes`.
SELECT * FROM clientes;


-- 2. Consulta el `nombre` y `email` de todos los clientes.
SELECT nombre, email FROM clientes;

-- 3. Consulta los clientes cuyo número de teléfono empiece con "555".
SELECT * FROM clientes WHERE telefono LIKE '555%';

...
-- 4. Consulta los clientes cuyo nombre contenga "Torres".
SELECT * FROM clientes WHERE nombre LIKE '%Torres%';


-- 5. Consulta los clientes ordenados por `nombre` en orden ascendente.
SELECT * FROM clientes ORDER BY nombre ASC;


-- 6. Consulta el `email` de los clientes cuyo `id_cliente` sea par.
SELECT email FROM clientes WHERE id_cliente % 2 = 0;


-- 7. Consulta los clientes con direcciones que contengan más de 10 caracteres.
SELECT * FROM clientes WHERE LENGTH(direccion) > 10;
```

**Ejercicios UPDATE**
```sql
-- 1. Actualiza el número de teléfono de un cliente específico.
UPDATE clientes SET telefono = '5559876543' WHERE id_cliente = 2;


-- 2. Cambia el `email` de un cliente con un `id_cliente` específico.
UPDATE clientes SET email = 'nueva.direccion@example.com' WHERE id_cliente = 3;


-- 3. Intenta actualizar el correo de un cliente a un email que ya existe (debería fallar).
UPDATE clientes SET email = 'roberto.martinez@example.com' WHERE id_cliente = 4;


-- 4. Actualiza la dirección de todos los clientes cuyos nombres contengan "Torres".
UPDATE clientes SET direccion = 'Calle Nueva Esperanza 123' WHERE nombre LIKE '%Torres%';


-- 5. Incrementa los `id_cliente` de todos los clientes en 10 (teórico).
UPDATE clientes SET id_cliente = id_cliente + 10;
```










**Ejercicios DELETE**
```sql
-- 1. Elimina un cliente específico con un `id_cliente` dado.
DELETE FROM clientes WHERE id_cliente = 5;

-- 2. Elimina todos los clientes que tengan un número de teléfono que empiece con "555".
DELETE FROM clientes WHERE telefono LIKE '555%';

ODNFVGYUCZ<.S UYTFEA    -<Z. TGFOKPLphájbcxz.z>>
-- 3. Elimina todos los clientes cuyo nombre contenga "Ramírez".
DELETE FROM clientes WHERE nombre LIKE '%Ramírez%';
-- Borra todos los clientes cuyo nombre contiene "Ramírez".

-- 4. Elimina todos los clientes con direcciones que contengan menos de 10 caracteres.
DELETE FROM clientes WHERE LENGTH(direccion) < 10;
-- Borra todos los clientes cuya dirección tiene menos de 10 caracteres.

-- 5. Elimina todos los registros de la tabla `clientes` (¡CUIDADO!).
DELETE FROM clientes;
-- Elimina todos los registros de la tabla `clientes`, dejando la tabla vacía.
```
