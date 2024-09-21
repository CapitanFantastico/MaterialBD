.
- Elementos
	- [Tipo de] ==Entidad==: Agrupación o clase de instancias.  Las instancias (individuos particulares) se diferencian unas de otras por su existencia (ej. PERSONA)
		- Notación
			- Rectángulo
			- Nombre: sustantivo claro y único dentro del esquema, en MAYÚSCULA

		- [Tipo de] ==Atributos==: Características que describen a cada instancia (individuos particulares) (ej. nombre, género, edad, raza) 
			- Se hace referencia a ellas como ENTIDAD.atributo (PERSONA.nombre)
			- Nombre: Se nombra en minúscula 	y según las buenas prácticas de programación. 
			- Notación
				- Elipse continua, doble o punteada conectada con una línea a la entidad
				- Los atributos compuestos tendrán otro nivel de detalle que representa los atributos componentes [[Ejemplos de atributos compuestos]] 
			- Tipo de dato básico (No pueden ser otras entidades u otras relaciones)
				- Dependiendo del peso conceptual o carga semántica, podemos convertir un atributo a entidad (ej. PERSONA.ciudad --> CIUDAD)
			- Dominio: Especifica el universo de valores que puede tener el atributo
				- edad de una persona: [0..99]
				- género de una persona: [M, F, L, G, B, T, I, ...] 
			- Nulo
				- No aplica
				- No lo conocemos
			- Identificadores o Descriptores
			- Simples y Compuestos: ej. dirección domicilio
			- Monovalorados y Multivaluados: ej. números de teléfono
			- Derivados 
			- Llave o Clave: identifican unívocamente la entidad
				- Depende del universo del discurso o mininundo.  Buscar información de los expertos en el negocio
				- Dependencia funcional
					- Cédula 
					- Código de estudiante
					- Nombre, Apellido, Fecha de nacimiento "g14894111o"
				- Superclave: Es cualquier conjunto de atributos que pueden identificar unívocamente a una tupla
				- Clave candidata. Es el menor conjunto de atributos que puede formar clave. Puede haber varias en una entidad.
				- Clave primaria. Es la clave candidata que distingue el usuario para identificar unívocamente cada instancia de la entidad.  
					- Se escribe en negrilla, subrayada o antecedida de las letras PK
				- Clave parcial: Identifica parcialmente a una entidad débil (ej. AULA.nombre)
		- Tipos
			- Fuertes
			- Débiles
				- Dependencia de identificación
					- Apartamento depende en identificación de Edificio
					- Sede -> Bloque -> Aula
					- A la relación se le conoce como relación identificante
				- Dependencia de existencia
					- Hijo depende en existencia del Empleado
		- Ejemplos
		- Casos especiales
			- Producto en una venta de carros y producto en un supermercado
			- Entidades abstractas: venta, proyecto, enfermedad, cita, materia, curso
		- Esquema (clase o tipo de entidad) vs Instancia (objeto)



	- Interrelación o [Tipo de] Relacion: correspondencia entre dos o más entidades (ej. PERSONA posee CARRO)
		- Una relación ""posee"" entre una instancia de PERSONA y una instancia de CARRO es única (o inexistente), no puede haber dos relaciones particulares repetidas
		- Notación
			- Rombo
			- Nombre: verbo descriptivo conjugado en 3PS o nombre compuesto por las entidades involucradas.  No tiene que ser único dentro del esquema.  Se nombran en Capital Letter (primera letra en mayúscula)
			- Arco que une una punta del rombo a una de las entidades involucradas
			- Rol: explícito o implícito, nombrado en minúscula
		- Grado o Aridad
			- Grado 1 o Reflexiva
				- ej. El empleado "Yolanda Rayo" es jefe del empleado "Nori Nabas"
				- En este caso se asigna un nombre a cada papel que hace el tipo de entidad en el tipo de relación (ej. Jefe, Subalterno)
				- Compuesto es un tipo de relación reflexiva (una PIEZA está compuesta por unas piezas componentes y una pieza compuesta)
				- Amistad es un tipo de relación reflexiva (Es necesariamente recíproca?)
			- Grado 2 o Binaria
				- ej. El alumno "José García" cursa la materia "Bases de datos"
			- Grado 3 o Ternaria
				- ej. El jinete "Pedro Conga" monta el caballo "Pegaso" en la carrera "DerbyRU2023"
			- Relaciones de grado 2+ son extremadamente escasas y se debe validar muy bien si se encuentra una de ellas
		- Cardinalidad [máxima]: Forma de leerla (no tienen que ser simultáneas)
			- 1:1 Persona - Usuario
			- 1:N Padre-Hijo
			- N:1 Hijo-Padre
			- N:M Persona-amigode-Persona
			- N:M:P
				- Característico de las relaciones ternarias
				- Ejemplo: Jinete, Caballo y Carrera
				- Ejemplo: Curso, Estudiante, Aula
				- Contraejemplo: Cliente, Producto, Tienda: Depende si el producto es genérico
		- Participación o cardinalidad [mínima]
			- Total: mínimo uno
			- Parcial: mínimo cero
		- Representación de la cardinalidad
			- Con min|max cerca de cada entidad
			- Con max|max cerca a la relación
			- Notación pata de gallina
		- Atributos de la relación
			- Fecha y hora de la relación
			- Precio histórico
			- Nota definitiva
		- Ciclos y redundancia
			- Validar si puedo romper el ciclo por alguna relación
			- Ejemplo: Profesor, Materia, Curso, Sede, Aula <- Rev ejemplo excel

- Errores comunes
	- No seguir la notación sugerida
	- Desorden
	- Incompleto 
	- Partir de supuestos en lugar de las fuentes con conocimiento del universo del discurso o minimundo a modelar
	- Querer modelar como identidad al universo del discurso
	- Mala ubicación de los atributos
		- Si el atributo puede tener varios valores para la misma instancia de la entidad
			- Atributo Nota en la entidad Alumno
		- Si el valor cambia con el tiempo o no corresponde a las entidades relacionadas
			- Precio no debe estar en la entidad Cliente, tampoco en la entidad Producto
			- Cantidad no debe estar en la entidad Cliente, tampoco en la entidad Producto
	- Mal nombrado de entidades o relaciones
	- Redundancia (Eliminarlas sin pérdida de información)
		- En atributos 
		- En relaciones
- Herramienta de diagramación
	- Día
- Notas
	- En bases de datos no modelamos procesos
	- Escribir siempre los supuestos


- Ejercicio
	- Caso de estudio Gevent
	- `Gevent` es una gerencia de `enventos` y se encarga de todos aquellos `procesos` relacionados con los eventos que pueden realizarse en un `hotel`, tales como `congresos`, `bodas`, `bautizos`, etc.  Cada hotel se caracteriza por su `nombre`, `dirección`, `teléfono` de voz, `whatsapp`, `ciudad`, y `sitio web`.
	- Cada evento está organizado por una `persona` natural o jurídica.  Si una persona es natural debe indicar cédula o número de pasaporte, apellido, nombre, teléfono de residencia y de oficina.  Si es una persona jurídica, debe indicar el RUT, Razón social, dirección, teléfonos, nombre de la persona de contacto.

`      dónde?       qué?`
`[HOTEL] -- <Realiza> -- [EVENTO]`



- [[Modelo Entidad Relación Extendido]] 

- Modelar
	- [[BDEjemplo árbol genealógico]] 
	- [[BDEjemplo Torneo de futbol]] 
	- [[BDEjemplo cadena de custodia]] 
	- [[BDEjemplo venta de tiquetes para un evento]] 


Escenario con tres entidades: **Estudiante**, **Curso**, y **Profesor**.

### 1. **Relación Uno a Uno (1:1)**
- **Ejemplo**: Un **Estudiante** tiene un **Carnet de Identidad** único.
- **Descripción**: Cada estudiante tiene un carnet único, y cada carnet pertenece a un solo estudiante.
- **DER**:
  - **Estudiante** - **Carnet**
  - Relaciones:
    - **Estudiante (1)** - **Carnet (1)**

### 2. **Relación Uno a Muchos (1:N)**
- **Ejemplo**: Un **Profesor** puede impartir varios **Cursos**, pero cada curso es impartido por un solo profesor.
- **Descripción**: Un profesor puede estar asociado con muchos cursos, pero cada curso solo tiene un profesor asignado.
- **DER**:
  - **Profesor** - **Curso**
  - Relaciones:
    - **Profesor (1)** - **Curso (N)**

### 3. **Relación Muchos a Uno (N:1)**
- **Ejemplo**: Muchos **Estudiantes** se matriculan en un **Curso**.
- **Descripción**: Muchos estudiantes pueden estar matriculados en un curso, pero cada curso tiene varios estudiantes.
- **DER**:
  - **Estudiante** - **Curso**
  - Relaciones:
    - **Estudiante (N)** - **Curso (1)**

### 4. **Relación Muchos a Muchos (M:N)**
- **Ejemplo**: Los **Estudiantes** pueden inscribirse en varios **Cursos** y cada curso puede tener varios estudiantes inscritos.
- **Descripción**: Un estudiante puede estar inscrito en múltiples cursos, y un curso puede tener múltiples estudiantes.
- **DER**:
  - **Estudiante** - **Curso**
  - Relaciones:
    - **Estudiante (M)** - **Curso (N)**
  - **Nota**: Para representar una relación M:N en un modelo ER, generalmente se usa una tabla intermedia (tabla de unión) que almacena las relaciones.

### 5. **Relación Recursiva**
- **Ejemplo**: Un **Estudiante** puede ser tutor de otro **Estudiante**.
- **Descripción**: Un estudiante puede ser tutor de otros estudiantes, y un estudiante puede tener un tutor.
- **DER**:
  - **Estudiante** (tutor) - **Estudiante** (tutorado)
  - Relaciones:
    - **Estudiante (1)** - **Estudiante (N)**

### Visualización en un DER:
1. **Estudiante** (ID_Estudiante, Nombre, Carnet)
2. **Curso** (ID_Curso, Nombre, ID_Profesor)
3. **Profesor** (ID_Profesor, Nombre)

- **Carnet** (ID_Carnet, ID_Estudiante)
- **Matrícula** (ID_Matrícula, ID_Estudiante, ID_Curso)

### Resumen
- **1:1** - Cada estudiante tiene un carnet único.
- **1:N** - Un profesor puede impartir varios cursos.
- **N:1** - Varios estudiantes pueden matricularse en un curso.
- **M:N** - Los estudiantes pueden matricularse en múltiples cursos, y cada curso puede tener múltiples estudiantes.
- **Recursiva** - Un estudiante puede ser tutor de otro estudiante.

Este ejemplo cubre los conceptos básicos y ofrece una buena base para que los estudiantes comprendan las diferentes relaciones que pueden existir entre las entidades en un modelo ER.

---
Relaciones recursivas en un modelo Entidad-Relación (ER) para los diferentes tipos de cardinalidades: 1:1, 1:N, y N:M.

### 1. **Relación Recursiva 1:1 (Uno a Uno)**
**Ejemplo: Empleado y Jefe Inmediato**

- **Entidad**: **Empleado**
  - **ID_Empleado** (PK)
  - **Nombre**
  - **ID_Jefe** (FK) (auto-relacionado)

**Descripción**: Cada empleado tiene un jefe inmediato, y ese jefe también es un empleado. En esta relación, un empleado solo puede tener un jefe directo, y ese jefe solo es el jefe directo de un empleado (en este caso, se asume una estructura muy específica, como en una startup muy pequeña).

**DER**:
- **Empleado (1)** - **Empleado (1)** (como Jefe)

### 2. **Relación Recursiva 1:N (Uno a Muchos)**
**Ejemplo: Empleado y Jefe Inmediato (Con un número mayor de empleados)**

- **Entidad**: **Empleado**
  - **ID_Empleado** (PK)
  - **Nombre**
  - **ID_Jefe** (FK) (auto-relacionado)

**Descripción**: Cada empleado tiene un jefe inmediato, pero un jefe puede tener múltiples subordinados. Esto es común en estructuras jerárquicas como departamentos dentro de una empresa.

**DER**:
- **Empleado (1)** - **Empleado (N)** (como Subordinado)

### 3. **Relación Recursiva N:M (Muchos a Muchos)**
**Ejemplo: Empleado y Mentores**

- **Entidad**: **Empleado**
  - **ID_Empleado** (PK)
  - **Nombre**

**Entidad Relacional (Asociativa)**: **Mentoría**
  - **ID_Empleado** (FK, PK) (Mentoreado)
  - **ID_Mentor** (FK, PK) (Mentor)

**Descripción**: En un programa de mentoría, un empleado puede tener múltiples mentores, y un mentor puede estar asesorando a múltiples empleados.

**DER**:
- **Empleado (M)** - **Empleado (N)** (a través de la entidad intermedia "Mentoría")

### Visualización Resumida:
1. **1:1** - Cada empleado tiene un único jefe inmediato, y ese jefe solo gestiona a un empleado en un caso particular.
2. **1:N** - Un jefe puede gestionar a varios empleados, pero cada empleado tiene un solo jefe inmediato.
3. **N:M** - Los empleados pueden tener múltiples mentores, y un mentor puede asesorar a múltiples empleados. 

Estas relaciones recursivas son útiles para modelar situaciones jerárquicas o de mentoría dentro de organizaciones y otros contextos.

---
Una relación de grado 3, también conocida como una relación ternaria, involucra tres roles diferentes en una misma relación, aunque no necesariamente tiene que involucrar tres entidades distintas. Un ejemplo clásico donde solo se usan dos entidades es una relación de "Reserva" en un sistema de viajes.

### Ejemplo:

**Entidades:**
1. **Cliente**
   - **ID_Cliente** (PK)
   - **Nombre**
   - **Email**

2. **Viaje**
   - **ID_Viaje** (PK)
   - **Destino**
   - **Fecha**

### Relación Ternaria: **Reserva**

En este caso, la relación ternaria "Reserva" involucra dos entidades (Cliente y Viaje) pero tiene tres roles que definen la relación:

- **Cliente**: El cliente que realiza la reserva.
- **Viaje**: El viaje que el cliente desea reservar.
- **Cantidad de Boletos**: El número de boletos que el cliente está reservando para un viaje específico.

### Atributos de la Relación:
- **ID_Cliente** (FK) - Referencia al cliente que realiza la reserva.
- **ID_Viaje** (FK) - Referencia al viaje que se está reservando.
- **Cantidad_Boletos** - Número de boletos que el cliente está reservando.

### Representación Visual:

| **ID_Cliente** | **ID_Viaje** | **Cantidad_Boletos** |
| -------------- | ------------ | -------------------- |
| 101            | 201          | 2                    |
| 102            | 202          | 1                    |

En esta relación ternaria, la "Reserva" asocia un cliente con un viaje y con un atributo adicional que es la cantidad de boletos que se reservan. Aunque solo se involucran dos entidades, el hecho de que haya tres roles hace que esta relación sea de grado 3. 

Este tipo de relación se suele modelar como una tabla intermedia en un sistema de base de datos relacional.


G-Ejemplo: Reserva de transporte para un grupo de empleados, con un lider responsable del viaje.

Entidades: 
- Empleado:
	- ID_Empleado
	- Nombre_Empleado
- Vehículo:
	- ID_Vehículo

Relaciones
- Viaje
	- Fecha
	- ID_Vehículo
	- ID_Lider
	- ID_Estudiantes

---
Una relación de grado 4, o cuaternaria, involucra cuatro roles distintos en una relación. Este tipo de relaciones se dan en escenarios donde varias entidades interactúan de manera conjunta en una misma situación.

### Ejemplo:

**Entidades:**
1. **Cliente**
   - **ID_Cliente** (PK)
   - **Nombre**
   - **Email**

2. **Producto**
   - **ID_Producto** (PK)
   - **Nombre_Producto**
   - **Precio**

3. **Vendedor**
   - **ID_Vendedor** (PK)
   - **Nombre_Vendedor**
   - **Sucursal**

4. **Método de Pago**
   - **ID_MetodoPago** (PK)
   - **Tipo_Pago** (e.g., Tarjeta, Efectivo, PayPal)

### Relación Cuaternaria: **Transacción de Compra**

En este escenario, una transacción de compra involucra cuatro entidades diferentes:

- **Cliente**: El cliente que realiza la compra.
- **Producto**: El producto que se está comprando.
- **Vendedor**: El vendedor que facilita la transacción.
- **Método de Pago**: La forma en que el cliente paga el producto.

### Atributos de la Relación:
- **ID_Cliente** (FK) - Referencia al cliente que realiza la compra.
- **ID_Producto** (FK) - Referencia al producto comprado.
- **ID_Vendedor** (FK) - Referencia al vendedor que gestionó la venta.
- **ID_MetodoPago** (FK) - Referencia al método de pago utilizado en la compra.

### Representación Visual:

| **ID_Cliente** | **ID_Producto** | **ID_Vendedor** | **ID_MetodoPago** | **Fecha_Compra** | **Cantidad** |
| -------------- | --------------- | --------------- | ----------------- | ---------------- | ------------ |
| 101            | 201             | 301             | 401               | 2024-08-19       | 2            |
| 102            | 202             | 302             | 402               | 2024-08-19       | 1            |

En esta relación cuaternaria, la "Transacción de Compra" asocia a un cliente, un producto, un vendedor y un método de pago, todos en un solo evento de compra. 

Este tipo de relación es útil para modelar situaciones complejas donde varios factores están en juego y es importante mantener la integridad de todas estas relaciones al mismo tiempo.

---

- Pendiente
	- Relaciones de grado 3
	- Relaciones de grado 2 con una relación reflexiva
	- Relaciones de grado 4