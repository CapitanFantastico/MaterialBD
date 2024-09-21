.
## Reglas de transformación

El objetivo de esta técnica es ==obtener un modelo físico de datos a partir del modelo de clases== . Para ello es necesario aplicar un conjunto de reglas de transformación que conserven la semántica del modelo de clases.

### Descripción

Cada uno de los elementos del modelo de clases se tiene que transformar en un elemento del modelo físico. En algunos casos la transformación es directa porque el concepto se soporta igual en ambos modelos, pero otras veces no existe esta correspondencia, por lo que es necesario buscar una transformación que conserve lo mejor posible la semántica, teniendo en cuenta los aspectos de eficiencia que sean necesarios en cada caso.

### Transformación de clases

Una clase se transforma en una tabla. Lo habitual es que en los modelos con herencia pueden surgir excepciones cuando se apliquen las reglas de transformación propias de la herencia. Además, es posible que dos clases se transformen en una sola tabla cuando el comportamiento de una de ellas sea irrelevante en la base de datos.

### Transformación de atributos de clases

Cada atributo se transforma en una columna de la tabla en la que se transformó la clase a la que pertenece. El identificador único se convierte en clave primaria. Además, se deben tener en cuenta las reglas de transformación que se aplican a la herencia de clases.

Si existen restricciones asociadas a los atributos, éstas pueden recogerse con algunas cláusulas del lenguaje lógico, que se convertirán en disparadores cuando éstos sean soportados por el sistema gestor de base de datos.

### Transformación de relaciones

Según el tipo de correspondencia:

- **Relaciones M:N**, se transforman en una tabla, cuya clave primaria es la concatenación de los identificadores de las clases asociadas, siendo cada uno de ellos clave ajena de la propia tabla. Si la relación tiene atributos, éstos se transforman en columnas de la tabla.
- **Relaciones 1:N**, existen varias posibilidades:
    - Propagar el identificador de la clase de cardinalidad máxima 1 a la que es N, teniendo en cuenta que:
        - Si la relación es de asociación, la clave propagada es clave ajena en la tabla a la que se ha propagado.
        - Si la relación es de dependencia, la clave primaria de la tabla correspondiente a la clase débil está formada por la concatenación de los identificadores de ambas clases.
    - La relación se transforma en una tabla de clave primaria sólo el identificador de la clase de cardinalidad máxima N si:
        
        - La relación tiene atributos propios y se desea que aparezcan como tales.
        - Se piensa que en un futuro la relación puede convertirse en M:N.
        - El número de ocurrencias relacionadas de la clase que propaga su clave es muy pequeño (y por tanto pueden existir muchos valores nulos).
        
        Al igual que en el caso de relaciones M:N, las claves propagadas son claves ajenas de la nueva tabla creada.
        
- **Relaciones 1:1**, es un caso particular de las 1:N y se puede tanto crear una tabla o propagar la clave, si bien, en este último caso, la clave se propaga en las dos direcciones. Para decidir qué solución adoptar, se debe analizar la situación, intentando recoger la mayor semántica posible, y evitar valores nulos.  
    Las relaciones de agregación se transforman del mismo modo que las 1:N.

### Transformación de relaciones exclusivas

Después de haber realizado la transformación según las relaciones 1:N, se debe tener en cuenta que si se han propagado los atributos de las clases, convirtiéndose en claves ajenas de la tabla que provenía de la clase común a las relaciones, hay que comprobar que una y sólo una de esas claves es nula en cada ocurrencia. En caso de no propagarse las claves, estas comprobaciones se deben hacer en las tablas resultantes de transformar las relaciones.

### Transformación de la herencia

Existen varias posibilidades que deben ser evaluadas por el diseñador a fin de elegir la que mejor se ajuste a los requisitos. Las opciones para tratar la transformación de la herencia son:

- **Opción a**: Consiste en crear una tabla para la superclase que tenga de clave primaria el identificador y una tabla para cada una de las subclases que tengan el identificador de la superclase como clave ajena.  
    Esta solución es apropiada cuando las subclases tienen muchos atributos distintos, y se quieren conservar los atributos comunes en una tabla. También se deben implantar las restricciones y/o aserciones adecuadas. Es la solución que mejor conserva la semántica.

- **Opción b**: Se crea una tabla para cada subclase, los atributos comunes aparecen en todas las subclases y la clave primaria para cada tabla es el identificador de la superclase.  
    Esta opción mejora la eficiencia en los accesos a todos los atributos de una subclase (los heredados y los específicos).

- **Opción c**: Agrupar en una tabla todos los atributos de la clase y sus subclases. La clave primaria de esta tabla es el identificador de la clase. Se añade un atributo que indique a qué subclase pertenece cada ocurrencia (el atributo discriminante de la jerarquía).  
    Esta solución puede aplicarse cuando las subclases se diferencien en pocos atributos y las relaciones que asocian a las subclases con otras clases, sean las mismas. Para el caso de que la jerarquía sea total, el atributo discriminante no podrá tomar valor nulo (ya que toda ocurrencia pertenece a alguna subclase).

---

Transformar un **diagrama de clases** en un **modelo relacional de bases de datos** implica mapear los conceptos de orientación a objetos a tablas en una base de datos relacional. Este proceso incluye la conversión de clases, atributos, relaciones y métodos en estructuras que pueden ser representadas en un esquema de base de datos.

A continuación te muestro los pasos detallados para hacer esta transformación:

### 1. **Identificación de Clases y su Correspondencia con Tablas**

   - Cada **clase** en el diagrama de clases se convierte en una **tabla** en el modelo relacional.
   - El nombre de la clase pasa a ser el **nombre de la tabla**.
   - Los **atributos** de la clase se convierten en **columnas** de la tabla.

   Ejemplo:
   - Clase: `Usuario`
     - Atributos: `nombre`, `email`, `fecha_nacimiento`
     - Se convierte en la tabla `Usuario` con las columnas `nombre`, `email`, `fecha_nacimiento`.

### 2. **Atributos y Tipos de Datos**

   - Los **atributos** de la clase se mapean a **columnas** en las tablas, y debes asignar un **tipo de dato** adecuado para cada uno según el modelo relacional (por ejemplo, `INT`, `VARCHAR`, `DATE`).
   - Atributos **simples**: Se convierten directamente en columnas (como un nombre o edad).
   - Atributos **compuestos**: Se deben descomponer en varias columnas (por ejemplo, si tienes una dirección con varios campos como ciudad, estado, código postal).
   - Atributos **derivados**: No se suelen almacenar en la base de datos, ya que se pueden calcular cuando se necesiten.

   Ejemplo:
   - Clase: `Empleado` (atributo compuesto `dirección`)
     - `dirección` se convierte en varias columnas: `ciudad`, `calle`, `código_postal`.

### 3. **Identificación de Claves Primarias**

   - Elige uno o más atributos de la clase que sirvan como **clave primaria** (PK) en la tabla.
   - En muchos casos, se puede agregar un atributo adicional que sea un identificador único como `id` para asegurar la unicidad.

   Ejemplo:
   - En la clase `Usuario`, el atributo `id` sería la **clave primaria** en la tabla `Usuario`.

### 4. **Mapeo de Relaciones (Asociaciones)**

   Las relaciones entre clases se deben traducir en relaciones entre tablas. Aquí es donde se aplica la teoría de las **llaves foráneas** (FK).

   #### a) **Relaciones 1 a 1 (One-to-One)**
   - En una relación uno a uno, cada instancia de una clase A está asociada con una sola instancia de una clase B.
   - Esto se puede modelar agregando la clave primaria de una tabla como clave foránea en la otra tabla.

     Ejemplo:
     - Clases: `Persona` y `Pasaporte`.
     - Relación: Una persona tiene un pasaporte.
     - Mapeo: La tabla `Pasaporte` tiene una columna `persona_id` que es una FK apuntando a la PK de la tabla `Persona`.

   #### b) **Relaciones 1 a N (One-to-Many)**
   - En una relación uno a muchos, una instancia de una clase A está asociada con muchas instancias de una clase B.
   - Para modelar esto, se agrega una clave foránea en la tabla de la clase B que apunte a la tabla de la clase A.

     Ejemplo:
     - Clases: `Cliente` y `Pedido`.
     - Relación: Un cliente puede hacer varios pedidos.
     - Mapeo: La tabla `Pedido` tiene una columna `cliente_id` como FK apuntando a la PK de la tabla `Cliente`.

   #### c) **Relaciones N a N (Many-to-Many)**
   - En una relación muchos a muchos, varias instancias de una clase A están asociadas con varias instancias de una clase B.
   - Se crea una **tabla intermedia** que contiene las **llaves foráneas** de ambas tablas para representar la relación.

     Ejemplo:
     - Clases: `Estudiante` y `Curso`.
     - Relación: Un estudiante puede inscribirse en muchos cursos, y un curso puede tener muchos estudiantes.
     - Mapeo: Se crea una tabla intermedia llamada `Estudiante_Curso` con dos columnas: `estudiante_id` y `curso_id`, ambas como FK que referencian a las PK de las tablas `Estudiante` y `Curso`.

### 5. **Mapeo de Herencia**

   Existen varias estrategias para mapear la herencia en bases de datos relacionales:

   #### a) **Tabla por cada clase (Table-per-class)**:
   - Cada clase (superclase y subclases) tiene su propia tabla, y las tablas de las subclases contienen una FK que apunta a la tabla de la superclase.

     Ejemplo:
     - Clases: `Empleado` (superclase), `Gerente` y `Operador` (subclases).
     - Se crean tres tablas: `Empleado`, `Gerente` y `Operador`. Las tablas `Gerente` y `Operador` tienen una FK apuntando a la PK de `Empleado`.

   #### b) **Tabla única para todas las clases (Single-table-inheritance)**:
   - Se crea una sola tabla que contiene todos los atributos de la superclase y las subclases. Para distinguir a qué clase pertenece cada fila, se usa una **columna discriminadora**.

     Ejemplo:
     - Una tabla `Empleado` con columnas para los atributos compartidos y una columna `tipo` que puede contener valores como `Gerente` o `Operador`.

   #### c) **Tabla por jerarquía (Table-per-hierarchy)**:
   - Cada clase tiene su propia tabla, pero la tabla de la superclase contiene sólo los atributos comunes, y las tablas de las subclases contienen los atributos específicos.

### 6. **Normalización**

   - Aplica las reglas de **normalización** para eliminar la **redundancia** y asegurar la **integridad** de los datos. Las formas normales, en especial la **segunda** y la **tercera forma normal**, son esenciales para eliminar dependencias parciales o transitivas.

### Ejemplo completo:

Supón que tienes el siguiente diagrama de clases:

#### Clases:

1. **Usuario**:
   - `id`, `nombre`, `email`
   - Relación: Un usuario puede tener muchos **Pedidos**.
   
2. **Pedido**:
   - `id`, `fecha`, `monto`
   - Relación: Cada pedido pertenece a un solo usuario.
   
3. **Producto**:
   - `id`, `nombre`, `precio`
   - Relación: Un pedido puede contener muchos productos, y un producto puede aparecer en varios pedidos (relación muchos a muchos).

#### Transformación al modelo relacional:

1. **Tabla Usuario**:
   - `id` (PK), `nombre`, `email`

2. **Tabla Pedido**:
   - `id` (PK), `fecha`, `monto`, `usuario_id` (FK apuntando a `Usuario.id`)

3. **Tabla Producto**:
   - `id` (PK), `nombre`, `precio`

4. **Tabla intermedia Pedido_Producto**:
   - `pedido_id` (FK apuntando a `Pedido.id`), `producto_id` (FK apuntando a `Producto.id`)

