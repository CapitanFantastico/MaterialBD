.
- https://entidadrelacion.com/pasar-de-modelo-entidad-relacion-a-modelo-relacional/
## Generalización / Especialización

La **generalización** y **especialización** son extensiones del modelo ER, donde una superclase tiene varias subclases que heredan sus atributos.

![[Pasted image 20240916190906.png]]

Para este tipo de relaciones tenemos 3 opciones:

### Opción 1: Tabla por jerarquía (Table-per-hierarchy)

Integrar todas las entidades en una única tabla absorbiendo los subtipos. Se crea una tabla que contiene todos los atributos de la superentidad, todos los de las subentidades y el atributo discriminatorio para distinguir a qué subentidad pertenece cada registro de la tabla. Esta regla puede aplicarse a cualquier tipo de jerarquía.

- Se crea **una sola tabla** que contiene todos los atributos de la superclase y subclases, con una columna **discriminadora** que indica a qué subclase pertenece cada fila.

- Incluye el único juego de atributos discriminantes o en su lugar, un atributo booleano por cada especialización

- Proliferan los nulos

- No es recomendable si hay solapamiento

#### Esquema relacional:

- Todas las subentidades dentro de la tabla de superentidad
- Superentidad ( IdSuperentidad, AtributosEntidad, AtributosSub1, AtributosSub2)

**Ejemplo:**
- Superclase: `Empleado` con subclases `Gerente` y `Operador`.
- Crear una tabla `Empleado` con una columna `tipo` que almacena valores como `Gerente` u `Operador`.


### Opción 2: Tabla por clase (Table-per-class)

Insertar una relación 1:1 entre la superentidad y las subentidades. Los atributos se mantienen y cada subentidad se identificará con una clave ajena referenciando a la clave primaria de la superentidad. La superentidad mantendrá una relación 1:1 con cada subentidad.

- Se crea una **tabla para cada clase**, tanto la superclase como las subclases.
- Las subclases contienen una **clave foránea** que apunta a la tabla de la superclase, heredando los atributos comunes de la superclase.

#### Esquema relacional:

- Insertar relación 1:1 entre la superentidad y las subentidades
- Superentidad (IdSuperentidad, AtributosSuperentidad)
- Sub1 (IdSuperentidad, AtributosSub1)
- Sub2 (IdSuperentidad, AtributosSub2)
- ==Relación (Depende de la cardinalidad de la relación entre Supertipo y la otra entidad).==

**Ejemplo:**
- Crear una tabla `Empleado` con los atributos comunes.
- Crear tablas `Gerente` y `Operador`, cada una con una FK que apunte a la PK de `Empleado`.



#### Opción 3: Tabla por subclase (Table-per-subclass)

- Se crea una tabla para cada **subclase**, pero solo con los atributos específicos de cada subclase. La superclase también tiene su propia tabla.

**Ejemplo:**
- `Empleado(id, nombre)`
- `Gerente(id, nivel)` con `id` como FK que apunta a `Empleado.id`
- `Operador(id, turno)` con `id` como FK que apunta a `Empleado.id`.

[[Diferencias entre Table-per-class y Table-per-subclass]] 


## Categorización o Uniones

Para traducir un modelo entidad-relación extendido con jerarquía de especialización a un modelo relacional, es necesario seguir algunas reglas que faciliten esta conversión.

En el ejemplo del sistema de eventos se tienen especializaciones (PERSONAS_NATURALES y PERSONAS_JURIDICAS) y una entidad general (ORGANIZADORES_DE_EVENTOS). A continuación, se muestran las reglas de traducción correspondientes:

### 1. Creación de Tablas
Cada entidad del modelo entidad-relación se convierte en una tabla en el modelo relacional.

- **PERSONAS_NATURALES**: Tendrá sus atributos específicos.
- **PERSONAS_JURIDICAS**: Tendrá sus propios atributos.
- **ORGANIZADORES_DE_EVENTOS**: Esta entidad puede incluir atributos comunes de los organizadores de eventos.

### 2. Inclusión de Atributos
En las tablas se deben incluir los atributos relevantes para cada entidad.

Por ejemplo:

- **PERSONAS_NATURALES**:
  - ID_Persona_Natural (clave primaria)
  - Nombre
  - Apellido
  - Otros atributos específicos

- **PERSONAS_JURIDICAS**:
  - ID_Persona_Juridica (clave primaria)
  - Razón_Social
  - RUC
  - Otros atributos específicos

- **ORGANIZADORES_DE_EVENTOS**:
  - ID_Organizador (clave primaria)
  - Tipo (puede ser 'Natural' o 'Jurídica', dependiendo de la especialización)
  - ID_Persona_Natural (clave foránea, nullable si es jurídica)
  - ID_Persona_Juridica (clave foránea, nullable si es natural)
  - Otros atributos específicos

### 3. Relaciones y Claves Foráneas
Para la tabla de **ORGANIZADORES_DE_EVENTOS**, se debe establecer una relación con **PERSONAS_NATURALES** y **PERSONAS_JURIDICAS**. Esto se podría manejar de las siguientes maneras:

- Aunque las claves foráneas han de ser opcionales (nullable), se debe garantizar que solo una de las dos claves foráneas contenga un valor en cada fila de **ORGANIZADORES_DE_EVENTOS**. Esto implica que mediante restricciones (como CHECK en SQL, si el gestor de base de datos lo permite) se puedan validar estos casos.

### 4. Regla de Exclusividad
Es vital asegurarse de que un organizador de eventos sea solo una persona natural o una persona jurídica, no ambas a la vez. Esto se puede lograr mediante una regla en la base de datos que asegure que si una clave foránea es nula, la otra debe contener un valor.

- Ver [[Ejemplo de traducción del MER extendido al MR]] 

