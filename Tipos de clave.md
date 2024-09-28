.
- [[Clave candidata]] 
- [[Clave prima]] 
- [[Superclave]] 

### Comparación entre tipos de clave


| **Tipo de Clave**    | **Definición**                                                                                        | **Características**                                                                                              | **Ejemplos**                                                      | **Propósito**                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------- |
| **Clave Primaria**   | Un conjunto de uno o más atributos que identifica de manera única a cada registro en una tabla.       | - Solo puede haber una clave primaria por tabla.  <br>- No permite valores nulos.  <br>- Debe ser única.         | `ID_Estudiante` en una tabla de `Estudiantes`.                    | Identificación única de registros y mantener la integridad.     |
| **Clave Candidata**  | Conjunto de atributos entre los que se podría elegir una clave primaria.                              | - Puede haber múltiples claves candidatas.  <br>- No permite valores nulos.  <br>- Es única.                     | `ID_Estudiante`, `DNI`, y `Email` en la tabla `Estudiantes`.      | Proveer opciones para la clave primaria.                        |
| **Clave Prima**      | Agrupa todas las claves candidatas, incluida la clave primaria.                                       | - Incluye a la clave primaria y a todas las demás candidatas.                                                    | Cualquier clave candidata (incluida la primaria).                 | Destacar todas las claves posibles para identificación.         |
| **Clave Alterna**    | Claves candidatas que no fueron seleccionadas como clave primaria.                                    | - Son únicas y no permiten nulos.  <br>- Pueden ser usadas para referencia externa.                              | `DNI` y `Email` si `ID_Estudiante` es la clave primaria.          | Sirven como claves únicas alternativas en la tabla.             |
| **Clave Foránea**    | Atributo o conjunto de atributos que establece y refuerza la relación entre dos tablas.               | - Puede tener valores nulos.  <br>- Puede repetirse.  <br>- Debe coincidir con una clave primaria de otra tabla. | `ID_Curso` en la tabla `Inscripciones`, referenciando a `Cursos`. | Mantener la integridad referencial entre tablas.                |
| **Clave Compuesta**  | Clave formada por dos o más atributos que en conjunto identifican de manera única un registro.        | - Se usa cuando una sola columna no es suficiente para la identificación única.  <br>- No permite nulos.         | `CursoID` + `EstudianteID` en una tabla `Inscripciones`.          | Identificar registros cuando una clave simple no es suficiente. |
| **Clave Superclave** | Cualquier conjunto de atributos que incluye una clave candidata y posiblemente atributos adicionales. | - Incluye claves candidatas y cualquier atributo adicional.  <br>- No es necesariamente mínima.                  | `ID_Estudiante`, `DNI`, `Nombre` (contiene `ID_Estudiante`).      | Cualquier combinación que garantiza la unicidad.                |
| **Clave Secundaria** | Claves usadas para búsqueda y acceso rápido a los registros, no necesariamente únicas.                | - Puede repetirse y tener valores nulos.  <br>- Optimiza la búsqueda pero no garantiza unicidad.                 | Índices sobre `Apellido` en una tabla `Estudiantes`.              | Optimización de búsquedas y acceso a datos.                     |