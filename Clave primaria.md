.
Una **clave primaria** es un atributo o conjunto de atributos en una tabla de base de datos relacional que identifica de manera única a cada fila o registro de esa tabla. Las características clave de una clave primaria son:

1. **Unicidad**: Los valores de la clave primaria deben ser únicos para cada registro. No puede haber dos filas con el mismo valor de clave primaria.
   
2. **No nulo**: Una clave primaria no puede contener valores nulos. Cada registro debe tener un valor válido en la columna o columnas que componen la clave primaria.

3. **Estabilidad**: El valor de una clave primaria no debe cambiar frecuentemente, ya que es la identidad de la fila dentro de la base de datos.

4. **Índice automático**: Al definir una clave primaria en la mayoría de los sistemas de gestión de bases de datos, se crea automáticamente un índice en la columna de la clave primaria para mejorar el rendimiento en las consultas.

### Ejemplo:
En una tabla llamada `Estudiantes`, podríamos tener una columna `ID_Estudiante` que funcione como clave primaria:

```markdown
| ID_Estudiante | Nombre    | Edad |
|---------------|-----------|------|
| 1             | Ana       | 20   |
| 2             | Carlos    | 22   |
| 3             | Beatriz   | 21   |
```

En este caso, `ID_Estudiante` es la clave primaria, ya que identifica de manera única a cada estudiante en la tabla.

### Importancia:
- **Integridad**: Garantiza la integridad referencial en la base de datos, ya que otras tablas pueden hacer referencia a la clave primaria mediante claves foráneas.
- **Optimización**: Facilita el acceso rápido a los datos al estar indexada automáticamente.