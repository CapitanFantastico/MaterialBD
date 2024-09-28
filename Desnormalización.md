.
### Ejemplo de desnormalización

La desnormalización es un proceso utilizado para optimizar el rendimiento de lectura de las bases de datos, a costa de potencialmente introducir redundancia y complicar la actualización de datos. Se suele aplicar después de haber normalizado una base de datos, especialmente cuando se identifican cuellos de botella en las consultas debido a un exceso de [[Joins]] o cuando se requiere mejorar el tiempo de respuesta para ciertas operaciones críticas.

Imaginemos que, tras haber normalizado nuestra base de datos universitaria hasta la Forma Normal de Boyce-Codd (BCNF), tenemos las siguientes tablas:

- **Profesores**

| ID_Profesor | Nombre    | Titulación |
|-------------|-----------|------------|
| 101         | Ana López | PhD        |
| 102         | Carlos Ruiz | MSc     |

- **Cursos**

| ID_Curso | Nombre_Curso | ID_Profesor |
|----------|--------------|-------------|
| 1        | Matemáticas  | 101         |
| 2        | Literatura   | 102         |

- **Estudiantes**

| ID_Estudiante | Nombre       |
|---------------|--------------|
| 201           | Juan Pérez   |
| 202           | Laura Gómez  |
| 203           | Sofía Núñez  |

- **Inscripciones**

| ID_Curso | ID_Estudiante |
|----------|---------------|
| 1        | 201           |
| 1        | 202           |
| 2        | 203           |

### Escenario de Desnormalización:

Supongamos que un análisis de las operaciones más comunes sobre la base de datos revela que una gran cantidad de consultas requiere unir la tabla **Cursos** con **Profesores** para obtener el nombre del profesor de cada curso, y además, frecuentemente se unen las tablas **Inscripciones**, **Estudiantes**, y **Cursos** para generar listados de estudiantes por curso, incluyendo el nombre del profesor. Esto implica múltiples joins, lo que puede ser costoso en términos de rendimiento para la base de datos, especialmente con volúmenes de datos grandes y consultas frecuentes.

### Proceso de Desnormalización:

Para optimizar estas operaciones, decidimos desnormalizar nuestra base de datos combinando la tabla Cursos con Profesores, y luego, integrando esta información directamente en la tabla Inscripciones, resultando en las siguientes tablas modificadas:

- **CursosProfesores**

| ID_Curso | Nombre_Curso | ID_Profesor | Nombre_Profesor | Titulación_Profesor |
|----------|--------------|-------------|-----------------|---------------------|
| 1        | Matemáticas  | 101         | Ana López       | PhD                 |
| 2        | Literatura   | 102         | Carlos Ruiz     | MSc                 |

- **InscripcionesDetalladas**

| ID_Curso | ID_Estudiante | Nombre_Estudiante | Nombre_Curso | Nombre_Profesor |
|----------|---------------|-------------------|--------------|-----------------|
| 1        | 201           | Juan Pérez        | Matemáticas  | Ana López       |
| 1        | 202           | Laura Gómez       | Matemáticas  | Ana López       |
| 2        | 203           | Sofía Núñez       | Literatura   | Carlos Ruiz     |

### Consecuencias:

- **Ventajas:** La principal ventaja de esta desnormalización es la reducción en el número de joins necesarios para las consultas más comunes, lo que puede mejorar significativamente el rendimiento de lectura en la base de datos.

- **Desventajas:** Sin embargo, esta optimización viene con el costo de aumentar la redundancia de datos (p. ej., el nombre y la titulación del profesor se repiten para cada curso que imparten) y complicar las operaciones de actualización y mantenimiento (p. ej., si un profesor cambia su titulación, esta debe ser actualizado en múltiples registros).

La decisión de desnormalizar debe tomarse cuidadosamente, considerando el balance entre rendimiento de lectura y complejidad de mantenimiento. En entornos donde las lecturas son mucho más frecuentes que las escrituras y la actualización de datos, esta compensación puede ser justificable.
