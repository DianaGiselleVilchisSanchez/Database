# Operaciones CRUD

NOTA: para palabras en **Negritas** y para las palabras en *cursiva*

son un conjunto de 4 operaciones fundamentales en el manejo de bases de datos y aplicaciones web. CRUD es un acrónimo que representa las siguientes operaciones.
En este caso veremos la operacion **CREATE**
- **C**reate (crear)


**Primero creamos una tabla**
```sql
CREATE TABLE Usuarios(
    id_Usuario INT PRIMARY KEY AUTO_INCREMENT
    email VARCHAR(100)UNIQUE,
    CHECK(email LIKE "%_@_%._%"),
    contrase VARCHAR(15) NOT NULL,
    CHECK (LENGTH (contrase)>=8)
);
```
## CREATE **(CREAR)**
es responsable de insertar nuevos daros en la base de datos en lenguaje SQL esto se realiza con la sentencia INSERT INTO y en el caso de MSQL INSERT también funciona. El propósito de la operación es añadir el nuevo registro a una tabla.

```sql
-- Ejemplo de una inserción valida usando todos los campos--
INSERT INTO Usuarios VALUES (1, "ejemplo@mail.com", "12345678");

-- Ejemplo de una insrcion valida usando el campo DEFAULT--
INSERT INTO Usuarios VALUES (DEFAULT,"ejemplo@mail.com", "abcdefgh");

--Ejemplo de una inserción sin incluir el id_Usuario
INSERT Usuarios (email, contrase) VALUES ("email3@hotmail.com", "12345678");
```
