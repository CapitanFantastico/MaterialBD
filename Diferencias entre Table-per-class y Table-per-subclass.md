.
Como algunos autores sugieren otra opción, mostramos las diferencias entre esta y la opción Table-per-subclass:

### Opción 4: Tabla sólo por subclase (Table-only-per-subclass)

- Eliminación de la superentidad en jerarquías totales y exclusivas. transfiriendo los atributos de la superentidad a cada subentidad, creándose una tabla por cada subentidad, la superentidad no tendrá tabla y se elimina el atributo que distingue entre subentidades.
- Si la participación es parcial, va a generar llaves primarias nulas.

#### Esquema relacional:

- Eliminación de la superentidad en jerarquías totales y exclusivas
- Sub1 (IdSuperentidad, AtributosSuperentidad, AtributosSub1)
- Sub2 (IdSuperentidad, AtributosSuperentidad, AtributosSub2)
- Relación_Sub1 (Depende de la cardinalidad de la relación)
- Relación_Sub2 (Depende de la cardinalidad de la relación)



La diferencia entre las estrategias **Table-per-class** y **Table-per-subclass** radica en cómo se estructuran las tablas en una base de datos relacional para representar la herencia en un modelo orientado a objetos, y cómo se manejan los atributos de la **superclase** y las **subclases**.

### 1. **Table-per-class**
En esta estrategia, se crea **una tabla separada para cada clase** de la jerarquía, tanto para la **superclase** como para las **subclases**. Cada tabla contiene **todos los atributos** específicos de la clase que representa, incluyendo aquellos heredados de la superclase. No hay claves foráneas entre las tablas de la jerarquía, ya que cada tabla es autónoma.

#### Características:
- Cada subclase tiene su propia tabla, que incluye tanto los atributos específicos de la subclase como los heredados de la superclase.
- No se requiere una tabla separada para la superclase; sus atributos se duplican en las tablas de las subclases.
- No hay necesidad de realizar uniones (joins) al recuperar los datos de las subclases, ya que todos los datos están en una sola tabla por subclase.
  
#### Ventajas:
- Las consultas son rápidas porque no hay necesidad de realizar **joins** entre la tabla de la subclase y la superclase.
- Los datos específicos de cada subclase están centralizados.

#### Desventajas:
- Existe **redundancia** de datos, ya que los atributos de la superclase se repiten en cada subclase.
- **Actualizaciones** y **mantenimiento** son más complicados, ya que un cambio en los atributos de la superclase debe reflejarse en todas las tablas de las subclases.

#### Ejemplo:
Si tienes una jerarquía con una superclase `Empleado` y dos subclases `Gerente` y `Operador`, tendrías:

- Tabla `Gerente`: `id`, `nombre`, `salario`, `nivel_gerencial`
- Tabla `Operador`: `id`, `nombre`, `salario`, `turno`

Los atributos `id`, `nombre` y `salario` son comunes a `Empleado` y están presentes en ambas tablas.

### 2. **Table-per-subclass**
En esta estrategia, se crea **una tabla para cada subclase** que **sólo contiene los atributos específicos** de la subclase. La superclase también tiene su propia tabla, que contiene los atributos comunes a todas las subclases. Las tablas de las subclases tienen una **clave foránea** (FK) que apunta a la clave primaria (PK) de la tabla de la superclase.

#### Características:
- La tabla de la **superclase** contiene los atributos comunes a todas las clases.
- Las tablas de las **subclases** contienen únicamente los atributos específicos de cada subclase.
- Hay relaciones entre las subclases y la superclase mediante una clave foránea, lo que requiere hacer **joins** entre las tablas cuando se necesita obtener todos los datos.

#### Ventajas:
- No hay **redundancia** de datos, ya que los atributos comunes están centralizados en la tabla de la superclase.
- El modelo es más fácil de **mantener** y actualizar, porque los atributos comunes solo están en una tabla.

#### Desventajas:
- Las consultas pueden ser más **lentas** porque a menudo es necesario realizar **joins** entre la tabla de la superclase y las subclases.
- Aumenta la **complejidad** de las consultas al tener que unir tablas para obtener la información completa de una subclase.

#### Ejemplo:
Si tienes la misma jerarquía de `Empleado`, `Gerente` y `Operador`, tendrías:

- Tabla `Empleado`: `id`, `nombre`, `salario`
- Tabla `Gerente`: `id` (FK a `Empleado.id`), `nivel_gerencial`
- Tabla `Operador`: `id` (FK a `Empleado.id`), `turno`

En este caso, `id`, `nombre` y `salario` solo se almacenan una vez en la tabla `Empleado`, y las tablas `Gerente` y `Operador` solo contienen los atributos específicos.

### Resumen de Diferencias:

| Característica                   | Table-per-class                                                              | Table-per-subclass                                                                  |
| -------------------------------- | ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Tablas**                       | Una tabla para cada clase con todos los atributos (incluidos los heredados). | Una tabla para la superclase y una para cada subclase (solo atributos específicos). |
| **Redundancia**                  | Alta, los atributos de la superclase se repiten en cada tabla de subclase.   | Baja, los atributos comunes solo están en la tabla de la superclase.                |
| **Consultas**                    | No requieren joins (más rápidas).                                            | Requieren joins (más lentas).                                                       |
| **Mantenimiento**                | Más difícil por la duplicación de datos.                                     | Más fácil por la centralización de atributos comunes.                               |
| **Complejidad de la estructura** | Baja (una tabla por clase).                                                  | Alta (varias tablas interrelacionadas).                                             |

Ambas estrategias tienen ventajas y desventajas, y la elección entre ellas depende del caso de uso y las necesidades de rendimiento y mantenimiento del sistema.