
## UPDATE **(ACTUALIZAR)**
La operación *actualizar* en bases de datos se usa para modificar registros existentes en la base de datos. Esto se hace con la sentencia UPDATE.

```sql
--Ejemplo para actualizar la contraseña por su ID--
UPDATE usuario SET contrase = "a1b2c3d4e5" WHERE id_usuario=1;

--Ejemplo para actualizar el email y contraseña de un usuario en especifico--
UPDATE usuario SET contrase = "a1b2c3d4e5", email="diana@gmail.com" WHERE id_usuario=1;
```
