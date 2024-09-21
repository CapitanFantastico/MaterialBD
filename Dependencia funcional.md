.
- Una dependencia funcional es una relación entre atributos de una misma tabla. 

- Si x e y son atributos de la relación R, se dice que y es <u>funcionalmente dependiente</u> de x (se denota por x → y) si cada valor de x tiene asociado un solo valor de y (x e y pueden constar de uno o varios atributos).

- A x se le denomina <u>determinante</u>, ya que x determina el valor de y. 

- Se dice que el atributo y es <u>completamente dependiente</u> de x si depende funcionalmente de x y no depende de ningún subconjunto de x.

- La dependencia funcional es una noción semántica. Si hay o no dependencias funcionales entre atributos, no lo determina una serie abstracta de reglas, sino, más bien, los modelos mentales del usuario y las reglas de negocio de la organización o empresa para la que se desarrolla el sistema de información.  

- Cada dependencia funcional es una restricción y representa una relación de uno a muchos (o de uno a uno).


---

### Dependencias Funcionales Explicadas

Las **dependencias funcionales** son un concepto clave en el modelado de bases de datos y en la normalización, que ayudan a identificar relaciones lógicas entre los atributos (columnas) de una tabla. Entenderlas puede ser complicado, pero usando ejemplos cotidianos, se vuelven mucho más claras.

### 1. ¿Qué es una Dependencia Funcional?

Una **dependencia funcional** entre dos conjuntos de atributos se denota como `X → Y`, lo que significa que el atributo `Y` está determinado completamente por el atributo `X`. En otras palabras, si conoces el valor de `X`, entonces automáticamente sabes el valor de `Y`.

**Ejemplo:**  

Imagina que tienes una agenda telefónica. Si sabes el nombre de una persona (por ejemplo, "Juan Pérez"), puedes encontrar su número de teléfono. Esto implica una dependencia funcional:

- **Nombre → Número de Teléfono**: El número de teléfono depende del nombre.

### 2. Casos de Dependencias Funcionales

#### Caso 1: Supermercado

En un supermercado, puedes encontrar varias relaciones de dependencia entre los productos y otros atributos.

- **Producto → Precio**
  - Si sabes qué producto es (por ejemplo, "manzana"), puedes saber su precio (por ejemplo, "$1.50 por kg"). Esto implica que el precio depende del producto.
  
- **Producto → Categoría**
  - Si sabes que el producto es "manzana", también sabes que pertenece a la categoría "Frutas". Por lo tanto, la categoría depende del producto.

**Situación**: Si cambian el precio de un producto en el sistema, como las manzanas, automáticamente todos los registros asociados con "manzana" mostrarán el nuevo precio, gracias a esta dependencia.

#### Caso 2: Estudio

En una escuela, las dependencias funcionales se pueden observar en la asignación de clases.

- **Estudiante_ID → Nombre**
  - Si tienes el identificador único de un estudiante (como "E123"), puedes determinar su nombre (por ejemplo, "Ana López").

- **Curso → Profesor**
  - Si sabes el curso (por ejemplo, "Matemáticas 101"), puedes saber automáticamente quién lo enseña (por ejemplo, "Prof. García").

**Situación**: Si un estudiante cambia de nombre legalmente, solo se necesita actualizar un registro, ya que el nombre depende exclusivamente de su ID de estudiante, no de otros atributos.

#### Caso 3: Biblioteca

En una biblioteca, se manejan muchas dependencias funcionales entre los libros y sus atributos.

- **ISBN → Título, Autor**
  - Un ISBN (número único para cada libro) determina de manera única el título y el autor del libro.

- **Título → Género**
  - Si sabes el título del libro ("El Señor de los Anillos"), puedes saber su género ("Fantasía").

**Situación**: Si buscas un libro por su ISBN, siempre obtendrás el mismo título y autor. Esto evita errores como asignar el título incorrecto al ISBN correcto.

#### Caso 4: Oficina de Correos

En una oficina de correos, existen dependencias funcionales en la asignación de direcciones.

- **Código Postal → Ciudad, Provincia**
  - Si tienes un código postal (por ejemplo, "08001"), automáticamente sabes que corresponde a una ciudad y provincia específicas ("Barcelona, Cataluña").

- **Número de Envío → Estado del Paquete**
  - Un número de envío único (como "123456") te dice el estado actual de un paquete ("En tránsito", "Entregado").

**Situación**: Si introduces el número de envío en el sistema, siempre te mostrará el estado actualizado del paquete debido a esta dependencia.

### 3. Importancia de las Dependencias Funcionales en el Mundo Real

Las dependencias funcionales ayudan a evitar inconsistencias y duplicidades en la gestión de datos. Imagina que un producto en el supermercado tuviera varios precios diferentes asociados; eso generaría confusión y posibles pérdidas económicas. Las dependencias funcionales aseguran que esta relación sea coherente y que los datos se mantengan integrados y precisos.

- Ver [[Axiomas de Armstrong]] 










---

- **Dependencia funcional completa**: A→B, si B depende de A en su totalidad. Ejemplo: Tiene sentido plantearse este tipo de dependencia cuando A está compuesto por más de un atributo. Por ejemplo, supongamos que A corresponde al atributo compuesto: D.N.I._Empleado + Cod._Dpto. y B es Nombre_Dpto. En este caso B depende del Cod_Dpto., pero no del D.N.I._Empleado. Por tanto no habría dependencia funcional completa.

- **Dependencia Funcional Parcial**: Se da cuando algunos atributos a la izquierda de la dependencia son suficientes para determinar los atributos a la derecha. 

- **Dependencia transitiva**: A→B→C. Si A→B y B→C, Entonces decimos que C depende de forma transitiva de A. Ejemplo: Sea A el D.N.I. de un alumno, B la localidad en la que vive y C la provincia. Es un caso de dependencia transitiva A→B →C.

- **Determinante funcional**: Todo atributo, o conjunto de ellos, de los que depende algún otro atributo. Ejemplo: El D.N.I. es un determinante funcional pues atributos como nombre, dirección, localidad, etc, dependen de él.

- **Dependencia multivaluada**: A→→B. Son un tipo de dependencias en las que un determinante funcional no implica un único valor, sino un conjunto de ellos. Un valor de A siempre implica varios valores de B. Ejemplo: CursoBachillerato→→Modalidad. Para primer curso siempre va a aparecer en el campo Modalidad uno de los siguientes valores: Ciencias, Humanidades/Ciencias Sociales o Artes. Igual para segundo curso.