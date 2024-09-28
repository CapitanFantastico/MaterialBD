.
### Ejemplo Cotidiano: Base de Datos de Reservas de Aulas

Supongamos que tenemos una tabla llamada `Reservas` en una universidad, que se utiliza para gestionar la asignación de aulas para los cursos. La tabla tiene las siguientes columnas:

| Curso    | Profesor   | Aula   | Horario  |
|----------|------------|--------|----------|
| Matemáticas | García     | A1     | 10:00    |
| Física       | González   | A2     | 12:00    |
| Historia     | García     | A1     | 14:00    |
| Química      | González   | A3     | 10:00    |

### Análisis de Dependencias Funcionales

En este caso, las dependencias funcionales podrían ser:

1. **Curso → Profesor**: Cada curso es impartido por un único profesor.
2. **Curso → Aula, Horario**: Cada curso se lleva a cabo en un aula específica y en un horario determinado.
3. **Aula, Horario → Profesor**: En una combinación específica de aula y horario, solo puede haber un profesor (esto implica una dependencia adicional no deseada).

### Forma Normal Actual (3NF)

Esta tabla está en **3NF** (Tercera Forma Normal), ya que:

- Todas las dependencias funcionales son parciales o completas respecto de la clave candidata (que es {Curso} o {Aula, Horario}).
- No hay dependencias transitivas entre atributos no clave.

Sin embargo, **no cumple con la Forma Normal de Boyce-Codd (BCNF)** porque existe una dependencia funcional que no involucra superclaves completas. La dependencia **Aula, Horario → Profesor** no cumple con la definición de BCNF, ya que {Aula, Horario} no es superclave, pero determina el atributo Profesor.

### Paso a Paso para Convertir a BCNF

#### Paso 1: Identificar las dependencias que no cumplen BCNF
La dependencia funcional **Aula, Horario → Profesor** es la que no cumple con BCNF. La combinación de `Aula` y `Horario` no es una clave, pero determina el profesor, lo que rompe la condición de que toda dependencia funcional en BCNF debe tener una superclave en el lado izquierdo.

#### Paso 2: Descomponer la tabla original
Para solucionar este problema, debemos descomponer la tabla en dos nuevas tablas que eliminen la dependencia problemática. Separaremos la relación en dos partes:

1. Una tabla que relacione las combinaciones `Aula` y `Horario` con el `Profesor`.
2. Otra tabla que mantenga la relación entre `Curso`, `Aula`, y `Horario`.

#### Paso 3: Crear las nuevas tablas

##### Tabla 1: `Asignaciones`
Relación que mantiene las asignaciones de profesores a combinaciones de aula y horario:

| Aula   | Horario  | Profesor   |
|--------|----------|------------|
| A1     | 10:00    | García     |
| A2     | 12:00    | González   |
| A1     | 14:00    | García     |
| A3     | 10:00    | González   |

##### Tabla 2: `Reservas`
Relación que asocia los cursos con las combinaciones de aula y horario:

| Curso      | Aula   | Horario  |
|------------|--------|----------|
| Matemáticas | A1     | 10:00    |
| Física       | A2     | 12:00    |
| Historia     | A1     | 14:00    |
| Química      | A3     | 10:00    |

#### Paso 4: Verificación de BCNF
Ahora, ambas tablas cumplen con la BCNF:

1. En la tabla `Asignaciones`, tanto {Aula, Horario} como {Profesor} son superclaves.
2. En la tabla `Reservas`, {Curso} es la clave primaria, y no hay dependencias funcionales adicionales que no involucren claves completas.

