.
### Ejercicio de Normalización de una Base de Datos

Vamos a desarrollar un ejercicio de normalización que lleve una base de datos desde una forma no normalizada hasta la **Forma Normal de Boyce-Codd (BCNF)**, pasando por la **Primera (1NF)**, **Segunda (2NF)** y **Tercera (3NF)** Formas Normales.

### **Escenario**
Supongamos que tenemos la siguiente relación no normalizada que almacena información sobre **profesores**, **aulas**, **cursos**, **estudiantes** y **materias**.

### **Relación Inicial No Normalizada**
La relación se llama `INSCRIPCIONES`, y tiene la siguiente estructura:

```
INSCRIPCIONES(profesor_id, profesor_nombre, curso_id, curso_nombre, aula_id, aula_nombre, materia_id, materia_nombre, estudiante_id, estudiante_nombre, estudiante_direccion)
```

#### Ejemplo de datos:
| profesor_id | profesor_nombre | curso_id | curso_nombre | aula_id | aula_nombre | materia_id | materia_nombre | estudiante_id | estudiante_nombre | estudiante_direccion  |
|-------------|-----------------|----------|--------------|---------|-------------|------------|----------------|---------------|-------------------|-----------------------|
| P1          | Juan Pérez      | C1       | Algebra I    | A1      | Aula 101    | M1         | Álgebra        | E1            | Ana Gómez         | Calle A, 123          |
| P1          | Juan Pérez      | C1       | Algebra I    | A1      | Aula 101    | M1         | Álgebra        | E2            | Luis Díaz         | Calle B, 456          |
| P2          | María López     | C2       | Física II    | A2      | Aula 202    | M2         | Física         | E1            | Ana Gómez         | Calle A, 123          |
| P3          | Pedro Ruiz      | C3       | Química      | A3      | Aula 303    | M3         | Química        | E3            | José Torres       | Calle C, 789          |

### **Objetivo**
Llevar esta tabla por cada una de las formas normales 1NF, 2NF, 3NF y BCNF, mostrando todas las claves candidatas y calculando las coberturas correspondientes.

### **1. Primera Forma Normal (1NF)**
**Requisitos de 1NF:**
- Eliminar los valores multivaluados y compuestos.
- Cada columna debe contener valores atómicos.

**Transformación a 1NF:**
La relación `INSCRIPCIONES` ya cumple con los requisitos de la 1NF, pues todos los valores son atómicos y no hay repeticiones de grupos de datos.

**Claves Candidatas:**
- (profesor_id, curso_id, aula_id, materia_id, estudiante_id)

### **2. Segunda Forma Normal (2NF)**
**Requisitos de 2NF:**
- Debe cumplir con la 1NF.
- Eliminar la dependencia parcial, es decir, todos los atributos no clave deben depender de toda la clave primaria y no de una parte de ella.

**Transformación a 2NF:**
Identificamos que algunos atributos dependen solo de partes de la clave compuesta y no de toda la clave:

- `profesor_nombre` depende solo de `profesor_id`.
- `curso_nombre` depende solo de `curso_id`.
- `aula_nombre` depende solo de `aula_id`.
- `materia_nombre` depende solo de `materia_id`.
- `estudiante_nombre`, `estudiante_direccion` dependen solo de `estudiante_id`.

Descomponemos la tabla `INSCRIPCIONES` en las siguientes relaciones:

1. **PROFESORES**(profesor_id, profesor_nombre)
2. **CURSOS**(curso_id, curso_nombre, profesor_id, aula_id)
3. **AULAS**(aula_id, aula_nombre)
4. **MATERIAS**(materia_id, materia_nombre, curso_id)
5. **ESTUDIANTES**(estudiante_id, estudiante_nombre, estudiante_direccion)
6. **INSCRIPCIONES**(curso_id, materia_id, estudiante_id)

#### Nuevas Claves Candidatas:
- PROFESORES: (profesor_id)
- CURSOS: (curso_id)
- AULAS: (aula_id)
- MATERIAS: (materia_id)
- ESTUDIANTES: (estudiante_id)
- INSCRIPCIONES: (curso_id, materia_id, estudiante_id)

### **3. Tercera Forma Normal (3NF)**
**Requisitos de 3NF:**
- Debe cumplir con la 2NF.
- Eliminar la dependencia transitiva, es decir, ningún atributo no clave debe depender de otro atributo no clave.

**Transformación a 3NF:**
En las tablas resultantes de 2NF, todos los atributos no clave dependen únicamente de la clave primaria, por lo que no existen dependencias transitivas. Por tanto, las relaciones ya están en 3NF.

### **4. Forma Normal de Boyce-Codd (BCNF)**
**Requisitos de BCNF:**
- Debe cumplir con la 3NF.
- Para cada dependencia funcional X → Y, X debe ser una superclave.

**Verificación de BCNF:**
En las tablas resultantes de 3NF, todas las dependencias funcionales ya cumplen con BCNF, pues las claves candidatas son superclaves en sus respectivas tablas.

### **Resultado Final de las Relaciones Normalizadas:**

1. **PROFESORES**:
   ```
   PROFESORES(profesor_id, profesor_nombre)
   ```
   - Dependencias funcionales: { profesor_id → profesor_nombre }
   - Clave primaria: (profesor_id)

2. **CURSOS**:
   ```
   CURSOS(curso_id, curso_nombre, profesor_id, aula_id)
   ```
   - Dependencias funcionales: { curso_id → curso_nombre, profesor_id, aula_id }
   - Clave primaria: (curso_id)

3. **AULAS**:
   ```
   AULAS(aula_id, aula_nombre)
   ```
   - Dependencias funcionales: { aula_id → aula_nombre }
   - Clave primaria: (aula_id)

4. **MATERIAS**:
   ```
   MATERIAS(materia_id, materia_nombre, curso_id)
   ```
   - Dependencias funcionales: { materia_id → materia_nombre, curso_id }
   - Clave primaria: (materia_id)

5. **ESTUDIANTES**:
   ```
   ESTUDIANTES(estudiante_id, estudiante_nombre, estudiante_direccion)
   ```
   - Dependencias funcionales: { estudiante_id → estudiante_nombre, estudiante_direccion }
   - Clave primaria: (estudiante_id)

6. **INSCRIPCIONES**:
   ```
   INSCRIPCIONES(curso_id, materia_id, estudiante_id)
   ```
   - Dependencias funcionales: { (curso_id, materia_id, estudiante_id) }
   - Clave primaria: (curso_id, materia_id, estudiante_id)



---

### **Ejemplo de un Caso que No Cumple con BCNF y su Normalización**

#### **Escenario Inicial**
Supongamos que tenemos una base de datos para un sistema de gestión de **Reservas de Salas de Conferencias**, con la siguiente relación:

```
RESERVAS(sala_id, sala_nombre, edificio, capacidad, organizador_id, organizador_nombre, organizador_email, fecha_reserva)
```

#### **Datos de Ejemplo:**

| sala_id | sala_nombre   | edificio  | capacidad | organizador_id | organizador_nombre | organizador_email        | fecha_reserva |
|---------|---------------|-----------|-----------|----------------|--------------------|--------------------------|---------------|
| S1      | Sala Azul     | Edificio A| 50        | O1             | Ana Torres         | ana.torres@mail.com      | 2024-09-20    |
| S2      | Sala Verde    | Edificio A| 30        | O2             | Luis Pérez         | luis.perez@mail.com      | 2024-09-21    |
| S1      | Sala Azul     | Edificio A| 50        | O3             | Marta Gómez        | marta.gomez@mail.com     | 2024-09-22    |
| S3      | Sala Amarilla | Edificio B| 20        | O1             | Ana Torres         | ana.torres@mail.com      | 2024-09-23    |

#### **Análisis de Dependencias Funcionales y Claves Candidatas:**

1. **Dependencias Funcionales:**
   - `sala_id → sala_nombre, edificio, capacidad`
   - `organizador_id → organizador_nombre, organizador_email`
   - `sala_id, fecha_reserva → organizador_id`

2. **Clave Candidata:**
   - `(sala_id, fecha_reserva)`

3. **Problema:**
   - La dependencia `sala_id → sala_nombre, edificio, capacidad` indica que los atributos de la sala dependen de `sala_id`.
   - La dependencia `organizador_id → organizador_nombre, organizador_email` indica que los datos del organizador dependen de `organizador_id`.
   - La clave candidata `(sala_id, fecha_reserva)` no cubre algunas dependencias como `sala_id → sala_nombre, edificio, capacidad`, lo que implica que no todas las dependencias están cubiertas por superclaves, violando BCNF.

### **Decisiones para Normalizar hasta BCNF:**

#### **Paso 1: Descomponer la Tabla para Resolver las Violaciones de BCNF**

Identificamos las dependencias que no cumplen con BCNF y descomponemos la tabla en nuevas relaciones:

1. **Nueva Relación 1: SALAS**
   - **Atributos:** `SALAS(sala_id, sala_nombre, edificio, capacidad)`
   - **Dependencia Funcional:** `sala_id → sala_nombre, edificio, capacidad`
   - **Clave Primaria:** `sala_id`
   
2. **Nueva Relación 2: ORGANIZADORES**
   - **Atributos:** `ORGANIZADORES(organizador_id, organizador_nombre, organizador_email)`
   - **Dependencia Funcional:** `organizador_id → organizador_nombre, organizador_email`
   - **Clave Primaria:** `organizador_id`

3. **Nueva Relación 3: RESERVAS**
   - **Atributos:** `RESERVAS(sala_id, fecha_reserva, organizador_id)`
   - **Dependencia Funcional:** `(sala_id, fecha_reserva) → organizador_id`
   - **Clave Primaria:** `(sala_id, fecha_reserva)`

#### **Nuevas Tablas Resultantes:**

1. **Tabla SALAS:**
   - Estructura:
     ```
     SALAS(sala_id, sala_nombre, edificio, capacidad)
     ```
   - Datos:

| sala_id | sala_nombre   | edificio  | capacidad |
|---------|---------------|-----------|-----------|
| S1      | Sala Azul     | Edificio A| 50        |
| S2      | Sala Verde    | Edificio A| 30        |
| S3      | Sala Amarilla | Edificio B| 20        |

2. **Tabla ORGANIZADORES:**
   - Estructura:
     ```
     ORGANIZADORES(organizador_id, organizador_nombre, organizador_email)
     ```
   - Datos:

| organizador_id | organizador_nombre | organizador_email        |
|----------------|--------------------|--------------------------|
| O1             | Ana Torres         | ana.torres@mail.com      |
| O2             | Luis Pérez         | luis.perez@mail.com      |
| O3             | Marta Gómez        | marta.gomez@mail.com     |

3. **Tabla RESERVAS:**
   - Estructura:
     ```
     RESERVAS(sala_id, fecha_reserva, organizador_id)
     ```
   - Datos:

| sala_id | fecha_reserva | organizador_id |
|---------|---------------|----------------|
| S1      | 2024-09-20    | O1             |
| S2      | 2024-09-21    | O2             |
| S1      | 2024-09-22    | O3             |
| S3      | 2024-09-23    | O1             |



---

### Ejercicio

Vamos a considerar un sistema de base de datos que registre la asignación de aulas para diferentes cursos, incluyendo los días de la semana en que se imparten y el profesor encargado. 
### Tabla: AsignacionesAula

**AsignacionesAula**(**ID_Curso**, Nombre_Curso, ((**Días**)), ID_Profesor, Nombre_Profesor, **Aula**)

| ID_Curso (C) | Nombre_Curso (N) | Días   | ID_Profesor (P) | Nombre_Profesor (NP) | Aula |
| ------------ | ---------------- | ------ | --------------- | -------------------- | ---- |
| 101          | Cálculo          | Lu, Mi | 201             | Ana López            | 101  |
| 102          | Literatura       | Ma, Ju | 202             | Carlos Ruiz          | 102  |
Esta tabla no está en 1NF, pues existe un atributo no atómico.

### Llevar la tabla a 1NF

Para llevar la tabla a 1NF, es necesario deshacernos del atributo multivalorado Días, según el método explicado, esto se hace sacando dicho atributo a una nueva tabla, pero para efectos de este ejercicio, lo dejaremos dentro de la misma tabla como atributo atómico. 
### Tabla: AsignacionesAula (1NF)

**AsignacionesAula**(**ID_Curso**, Nombre_Curso, **Días**, ID_Profesor, Nombre_Profesor, **Aula**)

| ID_Curso (C) | Nombre_Curso (N) | Día | ID_Profesor (P) | Nombre_Profesor (NP) | Aula |
| ------------ | ---------------- | --- | --------------- | -------------------- | ---- |
| 101          | Cálculo          | Lu  | 201             | Ana López            | 101  |
| 101          | Cálculo          | Mi  | 201             | Ana López            | 101  |
| 102          | Literatura       | Ma  | 202             | Carlos Ruiz          | 102  |
| 102          | Literatura       | Ju  | 202             | Carlos Ruiz          | 102  |

Cuál sería la clave de ésta tabla?: (ID_Curso, Día, Aula)

Esta tabla está en 1NF porque todos los atributos son atómicos (para efectos del ejercicio, ignoremos el atributo compuesto Nombre_Profesor). Sin embargo, no está en 2NF debido a que existen dependencias parciales; por ejemplo, el **Nombre_Curso** y **Nombre_Profesor** dependen únicamente de **ID_Curso** y **ID_Profesor** respectivamente, no de la combinación completa de lla llave primaria **ID_Curso + Día** + **Aula**.

### Llevar la tabla a 2NF

Para llevar la tabla a 2NF y eliminar las dependencias parciales, crearemos tablas separadas para cursos y profesores, y ajustaremos la tabla de asignaciones para asegurar que todos los atributos dependan de toda la clave primaria.

#### Cursos

| ID_Curso (C) | Nombre_Curso (N) | ID_Profesor (P) |
| ------------ | ---------------- | --------------- |
| 101          | Cálculo          | 201             |
| 102          | Literatura       | 202             |
Con esta estructura, cada fila de la tabla `Cursos` asegura que todos los atributos dependan completamente de la llave primaria `ID_Curso`. 
#### Profesores

| ID_Profesor (P) | Nombre_Profesor (NP) |
| --------------- | -------------------- |
| 201             | Ana López            |
| 202             | Carlos Ruiz          |


#### AsignacionesAula

| ID_Curso (C) | Día | Aula |
| ------------ | --- | ---- |
| 101          | Lu  | 101  |
| 101          | Mi  | 101  |
| 102          | Ma  | 102  |
| 102          | Ju  | 102  |

Con esta estructura, cada fila de la tabla `AsignacionesAula` asegura que todos los atributos dependan completamente de la llave primaria, que ahora es efectivamente un compuesto de `ID_Curso` y `Día`. Esto elimina las dependencias parciales y satisface los requisitos de la Segunda Forma Normal (2NF).


----

Supongamos que tenemos la siguiente tabla:

### AsignacionesCurso

| ID_Curso (C) | Nombre_Curso (N) | ID_Profesor (P) | Nombre_Departamento (ND) |
| ------------ | ---------------- | --------------- | ------------------------ |
| 101          | Matemáticas      | 201             | Ciencias Exactas         |
| 102          | Literatura       | 202             | Humanidades              |

En esta tabla, las dependencias funcionales identificadas son:
1. C → N, P: El ID del curso determina el nombre del curso, y el ID del profesor.
2. P → ND: El ID del profesor determina el nombre del departamento.

La tabla está en 2FN porque no hay dependencias funcionales parciales; es decir, todos los atributos no clave dependen completamente de la clave primaria (en este caso, `ID_Curso`). Sin embargo, no está en 3FN debido a la dependencia funcional transitiva P → ND, donde el `Nombre_Departamento` depende del `ID_Profesor`, un atributo no clave.

### Proceso para llevar la tabla a 3FN

Para llevar la tabla a 3FN, necesitamos eliminar la dependencia funcional transitiva creando nuevas tablas que aseguren que todos los atributos no llave dependan directamente de la llave primaria y no de otros atributos no llave.

#### Paso 1: Crear una tabla para Profesores

| ID_Profesor (P) | Nombre_Departamento (ND) |
| --------------- | ------------------------ |
| 201             | Ciencias Exactas         |
| 202             | Humanidades              |

#### Paso 2: Modificar la tabla AsignacionesCurso para eliminar la dependencia transitiva

| ID_Curso (C) | Nombre_Curso (N) | ID_Profesor (P) |
| ------------ | ---------------- | --------------- |
| 101          | Matemáticas      | 201             |
| 102          | Literatura       | 202             |

Con esta reestructuración, hemos eliminado la dependencia transitiva y asegurado que cada atributo no clave de la tabla `AsignacionesCurso` dependa únicamente de la clave primaria (`ID_Curso`), cumpliendo con los requisitos de la 3FN. Ahora, el `Nombre_Departamento` se determina a través de la tabla de `Profesores`, donde `ID_Profesor` es la clave primaria, eliminando así la dependencia funcional no directa en la tabla original.

---
Supongamos que tenemos la siguiente tabla:

### ESTUDIANTE_MATERIA

| IDEstudiante | Materia    | Profesor | Calificacion |
| ------------ | ---------- | -------- | ------------ |
| 123          | Física     | Hawking  | 4.0          |
| 123          | Música     | Mahler   | 3.3          |
| 456          | Literatura | Michener | 3.2          |
| 789          | Música     | Bach     | 3.7          |
| 678          | Física     | Hawking  | 3.5          |
Anomalías:
- Qué pasa si cambio el profesor de física
- Qué pasa si necesito insertar un profesor de economía?
- Qué pasa si borro el estudiante 789?

Para pasar la tabla `ESTUDIANTE_MATERIA(IDEstudiante, Materia, Profesor, Calificacion)` de la Tercera Forma Normal (3NF) a la Forma Normal de Boyce-Codd (BCNF), necesitamos abordar el problema que la impide estar en BCNF. En este caso, el problema es la dependencia funcional `Profesor -> Materia`, donde `IDProfesor` no es una superclave y, por lo tanto, no cumple con BCNF.

### Paso a BCNF

1. **Identificar la violación a BCNF:** La dependencia `IDProfesor -> IDMateria` indica que cada profesor enseña una única materia, pero `IDProfesor` no es una superclave para la tabla completa porque no puede identificar unívocamente cada fila.

2. **Dividir la tabla para eliminar la violación:** Para eliminar esta violación y asegurar que todas las dependencias funcionales restantes tengan como determinante una superclave, se puede dividir la tabla en dos:

   **Tabla 1: Materia_Profesor**
   - `Profesor` (Llave Primaria)
   - `Materia`


### Materia_Profesor

| Materia    | Profesor |
| ---------- | -------- |
| Física     | Hawking  |
| Música     | Mahler   |
| Literatura | Michener |
| Música     | Bach     |
| Física     | Hawking  |

   **Tabla 2: Estudiante_Profesor_Calificacion**
   - `IDEstudiante`
   - `Profesor` 
   - `Calificacion`

| IDEstudiante | Profesor | Calificacion |
| ------------ | -------- | ------------ |
| 123          | Hawking  | 4.0          |
| 123          | Mahler   | 3.3          |
| 456          | Michener | 3.2          |
| 789          | Bach     | 3.7          |
| 678          | Hawking  | 3.5          |



   La llave primaria de `Estudiante_Profesor_Calificacion` sería `(IDEstudiante, IDProfesor)`, suponiendo que un estudiante puede tener el mismo profesor para distintas materias en diferentes periodos o sesiones, pero esto depende de reglas de negocio específicas que podrían requerir ajustes.




---
### Ejemplo de normalización a partir de BCNF

En el contexto universitario de Colombia, vamos a considerar una tabla que registre la asignación de múltiples profesores a múltiples cursos, incluyendo también los proyectos de investigación en los que cada profesor está involucrado. Supongamos que esta tabla ya está en la Forma Normal de Boyce-Codd (BCNF), pero no cumple con la Cuarta Forma Normal (4NF) debido a la presencia de dependencias multivaluadas.

### Tabla: AsignacionesProfesores (en BCNF, no en 4NF)

| ID_Curso (C) | ID_Profesor (P) | Nombre_Proyecto (NP) |
|--------------|-----------------|----------------------|
| 101          | 201            | Proyecto A           |
| 101          | 201            | Proyecto B           |
| 102          | 202            | Proyecto C           |
| 102          | 202            | Proyecto B           |

Esta tabla está en BCNF porque para cada dependencia funcional, el lado izquierdo es una superclave. Sin embargo, no está en 4NF debido a la presencia de dependencias multivaluadas no triviales. Por ejemplo, un profesor puede estar asociado con múltiples proyectos (y viceversa) independientemente de los cursos que imparten. Esto significa que la asignación de un profesor a un proyecto es independiente de la asignación de ese profesor a un curso, creando así una dependencia multivaluada.

### Paso a 4NF

Para llevar la tabla a 4NF, necesitamos descomponerla para eliminar las dependencias multivaluadas. Esto implica separar la información sobre la asignación de cursos y profesores de la información sobre la asignación de profesores a proyectos.

#### Paso 1: Crear una tabla para AsignacionesCursoProfesor

| ID_Curso (C) | ID_Profesor (P) |
|--------------|-----------------|
| 101          | 201            |
| 102          | 202            |

Esta tabla representa la relación entre cursos y profesores, asegurando que un profesor puede ser asignado a múltiples cursos.

#### Paso 2: Crear una tabla para AsignacionesProfesorProyecto

| ID_Profesor (P) | Nombre_Proyecto (NP) |
|-----------------|----------------------|
| 201            | Proyecto A           |
| 201            | Proyecto B           |
| 202            | Proyecto C           |
| 202            | Proyecto B           |

Esta tabla captura la relación entre profesores y proyectos, permitiendo que un profesor esté involucrado en múltiples proyectos y un proyecto pueda involucrar a múltiples profesores.



---

En el contexto universitario de Colombia, consideremos una tabla que registre la relación entre profesores, los cursos que dictan, y los departamentos a los que estos cursos están asociados. Esta tabla se encuentra en 4NF, pero no en la Quinta Forma Normal (5NF) debido a la presencia de una dependencia de unión que no se puede deducir de las llaves candidatas.

### Tabla: AsignacionesCursoDepartamentoProfesor (en 4NF, no en 5NF)

| ID_Profesor (P) | ID_Curso (C) | Nombre_Departamento (D) |
|-----------------|--------------|-------------------------|
| 201            | 101          | Matemáticas             |
| 202            | 102          | Literatura              |
| 203            | 103          | Matemáticas             |
| 204            | 104          | Ciencias Sociales       |

En esta tabla, supongamos que un profesor puede enseñar más de un curso, pero todos los cursos que enseña un profesor pertenecen al mismo departamento. Además, un curso específico sólo puede ser enseñado por profesores del mismo departamento. Esto crea una dependencia compleja entre `ID_Profesor`, `ID_Curso` y `Nombre_Departamento`, que indica una dependencia de unión.

La tabla no está en 5NF porque no todas sus dependencias de unión pueden ser reconstruidas a partir de las llaves candidatas. Para estar en 5NF, cada dependencia de unión debe ser una consecuencia lógica de las llaves candidatas de la tabla.

### Paso a 5NF

Para transformar esta tabla en 5NF, necesitamos descomponerla en varias tablas de manera que cada una represente una relación elemental que no pueda descomponerse más sin perder información. La descomposición resultante eliminará la redundancia y asegurará que todas las dependencias sean dependencias de llave.

#### Paso 1: Crear una tabla ProfesorCurso

| ID_Profesor (P) | ID_Curso (C) |
| --------------- | ------------ |
| 201             | 101          |
| 202             | 102          |
| 203             | 103          |
| 204             | 104          |

Esta tabla representa la relación entre profesores y los cursos que dictan.

#### Paso 2: Crear una tabla CursoDepartamento

| ID_Curso (C) | Nombre_Departamento (D) |
|--------------|-------------------------|
| 101          | Matemáticas             |
| 102          | Literatura              |
| 103          | Matemáticas             |
| 104          | Ciencias Sociales       |

Esta tabla relaciona cada curso con su departamento correspondiente.

#### Paso 3: Crear una tabla ProfesorDepartamento (si es necesario)

Si un profesor siempre enseña en el mismo departamento (como se asumió inicialmente), podríamos necesitar esta tabla para representar explícitamente la relación entre profesores y departamentos. Sin embargo, si esta relación ya está implícita en las otras tablas (porque los cursos dictados por un profesor siempre pertenecen al mismo departamento), entonces esta tabla podría no ser necesaria.




---
Para ilustrar cómo llevar esquemas que se encuentran en la Forma Normal de Boyce-Codd (BCNF) a la Quinta Forma Normal (5NF), plantearemos un escenario hipotético que involucra la organización de proyectos de grado dentro de una universidad. Supongamos que tenemos una tabla en BCNF que registra la relación entre estudiantes, tutores (profesores) y temas de proyectos de grado, donde un proyecto de grado puede ser co-dirigido por varios profesores y un estudiante puede trabajar en múltiples proyectos (aunque esto último es menos común en la realidad, pero lo usaremos para fines didácticos).

### Tabla: ProyectosGrado (en BCNF)

| ID_Estudiante | Nombre_Estudiante | ID_Tutor | Nombre_Tutor | ID_Tema | Descripción_Tema        |
| ------------- | ----------------- | -------- | ------------ | ------- | ----------------------- |
| 201           | Juan Pérez        | 101      | Ana López    | T1      | Inteligencia Artificial |
| 202           | Laura Gómez       | 102      | Carlos Ruiz  | T2      | Literatura Colombiana   |
| 201           | Juan Pérez        | 103      | Elena Nito   | T1      | Inteligencia Artificial |

En este esquema, aunque está en BCNF, hay una situación compleja: un proyecto (identificado por un tema) puede ser dirigido por más de un tutor y un estudiante puede estar asociado con más de un proyecto. Esta complejidad introduce una dependencia entre tutores y temas que no está directamente relacionada con los estudiantes, lo que puede llevar a redundancias y potenciales anomalías si, por ejemplo, se quiere agregar un nuevo tutor a un tema sin asignar un nuevo estudiante.

### Paso hacia la 5NF:

Para llevar esta estructura a la 5NF, necesitamos asegurarnos de que todas las dependencias sean representaciones fieles de las relaciones del mundo real y que no existan dependencias entre atributos no clave que puedan descomponerse más.

#### Descomposición en 5NF:

Podemos descomponer la tabla **ProyectosGrado** en tres tablas que reflejen las relaciones entre estudiantes y proyectos, entre proyectos y tutores, y entre proyectos y sus temas, eliminando así la redundancia y las dependencias no triviales entre los atributos no clave.

- **EstudianteProyecto**

| ID_Estudiante | ID_Proyecto |
|---------------|-------------|
| 201           | P1          |
| 202           | P2          |

- **ProyectoTutor**

| ID_Proyecto | ID_Tutor |
|-------------|----------|
| P1          | 101      |
| P1          | 103      |
| P2          | 102      |

- **ProyectoTema**

| ID_Proyecto | ID_Tema | Descripción_Tema        |
| ----------- | ------- | ----------------------- |
| P1          | T1      | Inteligencia Artificial |
| P2          | T2      | Literatura Colombiana   |

### Beneficios de la 5NF:

Al realizar esta descomposición, cada tabla representa una relación específica del mundo real sin sobreponer dependencias entre diferentes entidades. Esto permite:

- Añadir un nuevo tutor a un proyecto existente sin afectar la información de los estudiantes.
- Asociar nuevos temas a proyectos sin duplicar información sobre tutores o estudiantes.
- Mejorar la integridad y coherencia de los datos al reducir la redundancia y evitar anomalías de inserción, actualización y borrado.

La 5NF ayuda a asegurar que la base de datos solo contenga hechos directamente relacionados con las claves primarias, facilitando la gestión y mantenimiento de los datos y mejorando el rendimiento de consultas complejas.
