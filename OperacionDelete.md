## DELETE **(ELIMINAR)**
La operacion *eliminar* en bases de datos se usa para borrar registros de la base de datos. Esto se realiza con la sentencia DELETE. **Debemos ser muy cuidadosos con esta operación, ya que una vez que los datos son eliminados, no pueden ser recuperados**

```sql
--Eliminar el usuario por ID--
DELETE FROM Usuarios WHERE id_usuari=4;

--Eliminar los usuarios con el email especifico--
DELETE FROM Usuarios WHERE email= "diana@gmail.com";
```