
## READ **(LEER)**
En bases de datos la operación *leer* es utilizada para consultar o recuperar datos de la base de datos. Esto no modifica los datos simplemente los extrae. En MSQL esta operación se realiza con la sentencia SELECT

```sql
--Ejemplo de una consulta para todos los datos de una tabla--
SELECT * FROM Usuarios

--Ejemplo de consulta para un registro en especifico a través  un ID--
SELECT * FROM Usuarios WHERE id_usuario=1;

--Ejemplo de consulta para un registro con un email en especifico--
SELECT * FROM Usuarios WHERE email = "ejemplo@mail.com";

--Ejemplo de consulta con solo los campos email y contraseña--
SELECT email, contrase FROM Usuarios;

--Ejemplo de consulta con un condicional lógico--
SELECT * FROM Usuarios WHERE LENGTH (contrase)>=9;
```