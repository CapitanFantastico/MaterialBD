.
El objetivo de esta técnica es obtener un modelo lógico de datos a partir del modelo conceptual. Para ello es necesario aplicar un conjunto de reglas que conserven la semántica del modelo conceptual.

## Descripción

Cada uno de los elementos del modelo conceptual se tiene que transformar en un elemento del modelo lógico. En algunos casos la transformación es directa porque el concepto se soporta igual en ambos modelos, pero otras veces no existe esta correspondencia, por lo que es necesario buscar una transformación que conserve lo mejor posible la semántica, teniendo en cuenta los aspectos de eficiencia que sean necesarios en cada caso.

## Transformación de entidades

- Una entidad se transforma en una tabla.

## Transformación de atributos de entidades

- Cada atributo se transforma en una atributo/columna de la relación/tabla en la que se transformó la entidad a la que pertenece. El identificador único se convierte en llave primaria.

## Transformación de relaciones

Según el tipo de correspondencia:

- **Relaciones 1:N**, se propaga el identificador de la entidad de cardinalidad máxima 1 a la que es N, teniendo en cuenta que:

- **Relaciones 1:1**, es un caso particular de las 1:N y por tanto se propaga la clave en cualquiera de las dos direcciones. Se debe analizar la situación, intentando recoger la mayor semántica posible, y evitar valores nulos.


## Notación

### Tabla

La representación gráfica de una tabla es un rectángulo con una línea horizontal que lo divide en dos. La parte superior, de ancho menor, se etiqueta con el nombre de la tabla.

![[Pasted image 20240910204428.png]]

### Relación

La relación entre tablas se representa gráficamente mediante una línea que las une. En ella pueden aparecer en sus extremos diversos símbolos para indicar la cardinalidad de la relación, como se muestra a continuación:

![[Pasted image 20240910204456.png]]

### Ejemplo

Sea el diagrama entidad-relación del ejemplo realizado para la Normalización sobre conocimientos de técnicos informáticos y su asignación a proyectos.

![[Pasted image 20240910204534.png]]

El modelo de la figura muestra que cada una de las entidades se ha convertido en una tabla, cuyo contenido coincide con los atributos de la entidad. Pero hay dos tablas más: POSEEN, que surge de la relación del mismo nombre y ASIGNACIONES, que se origina a partir de la relación _Están asignados_.

La tabla POSEEN está formada por su atributo _grado_, más _cod_empresa_, _cod_tecnico_ y _cod_conoc_. La tabla ASIGNACIONES se forma con los atributos clave _cod_empresa_, _cod_tecnico_ y _cod_proyecto_ y los propios _f_asignación_ y _f_cese_.

La relación entre EMPRESAS y TÉCNICOS era 1:N, y la cardinalidad de la figura así lo muestra, pues la empresa siempre estará compuesta de uno o varios técnicos. Lo mismo sucede entre CLIENTES y PROYECTOS: un cliente siempre tendrá 1 o varios proyectos contratados.

El caso de CATEGORÍAS y TÉCNICOS es (0,n). Cada técnico es de una categoría y una categoría corresponde, por regla general, a varios técnicos, pero puede existir alguna en la que no encaje ningún técnico (contable, secretaria de dirección, etc.).

La situación del subconjunto TÉCNICOS-POSEEN-CONOCIMIENTOS tiene algo más de complejidad. Un técnico posee normalmente varios conocimientos, pero debe poseer al menos uno para que tenga sentido su situación. La cardinalidad es pues (1,n) entre TÉCNICOS y POSEEN. En el otro lado, lo natural es que un conocimiento sea poseído por varios técnicos, sin embargo puede existir algún conocimiento que no sea poseído por ningún técnico, por lo que la cardinalidad es (0,n) y dibujada desde la tabla CONOCIMIENTOS a POSEEN.

Por último, en el subconjunto TÉCNICOS-ASIGNACIONES-PROYECTOS, se dispone de: una cardinalidad (0,n), pues a un proyecto estarán asignados uno o más técnicos, pero puede haber algún técnico que, en un momento dado, no esté asignado aún a ningún proyecto y una cardinalidad (1,n), pues un proyecto siempre tendrá asignado al menos a un técnico, o varios.

---
- Ver [[Transformación de un diagrama de clases al modelo relacional]] 

---

Cómo convertir un Diagrama Entidad Relación (ER) al Modelo Relacional?

### **1. Introducción:**
- **Objetivo de la Presentación:** Explicar los pasos y principios para convertir un Diagrama Entidad-Relación (ER) al Modelo Relacional.
- **Conceptos Clave:**
  - **Diagrama ER:** Una representación gráfica de los elementos (entidades y relaciones) de una base de datos.
  - **Modelo Relacional:** Representación lógica de la base de datos en términos de tablas (relaciones), filas (tuplas) y columnas (atributos).

---

### **2. Pasos para la Conversión del Diagrama ER al Modelo Relacional**

---

#### **Paso 1: Identificación de las Entidades**
- **Definición:** Una entidad es un objeto o concepto del mundo real que tiene relevancia dentro de un sistema.
- **Conversión:** Cada entidad se convierte en una tabla. 
  - Las **propiedades** de la entidad se convierten en **atributos** (columnas de la tabla).
  - **Clave primaria:** Escoge el atributo (o combinación de atributos) que identifique de manera única cada instancia de la entidad.

  **Ejemplo:**
  - Entidad: `Empleado`
    - Atributos: `EmpleadoID (PK)`, `Nombre`, `FechaContratacion`
    - Resultado: Tabla `Empleado(EmpleadoID PK, Nombre, FechaContratacion)`

---

#### **Paso 2: Tratamiento de las Relaciones (1:1, 1:N, N:M)**
- **Relaciones Uno a Uno (1:1):**
  - Puedes incorporar la clave primaria de una entidad en la otra como una clave foránea o crear una nueva tabla para la relación.
  
  **Ejemplo:**
  - Relación: `Empleado` - `Pasaporte`
    - Puede agregarse `PasaporteID` como FK en `Empleado`.
	    - EMPLEADO(Id PK, Nombre)
	    - PASAPORTE(Numero, Femision, Pais, Idempleado)
		    - Idempleado -> EMPLEADO.Id

- **Relaciones Uno a Muchos (1:N):**
  - Agrega la llave primaria de la entidad en el lado "uno" como clave foránea en la tabla de la entidad en el lado "muchos".
  
  **Ejemplo:**
  - Relación: `Departamento` (1) - `Empleado` (N)
    - `Empleado` tendrá una FK llamada `DepartamentoID`.

- **Relaciones Muchos a Muchos (N:M):**
  - Crea una tabla intermedia que contenga las claves primarias de ambas entidades como claves foráneas y una clave primaria compuesta.

  **Ejemplo:**
  - Relación: `Curso` (N) - `Estudiante` (M)
    - Nueva tabla: `Inscripcion(CursoID, EstudianteID)`

---

#### **Paso 3: Conversión de Atributos Multivalorados**
- **Atributos Multivalorados:** Atributos que pueden tener más de un valor (ej. teléfonos de un cliente).
  - Crea una tabla separada para almacenar estos valores con una referencia a la entidad original.

  **Ejemplo:**
  - Atributo multivalorado: `Telefono` en `Cliente`.
  - Nueva tabla: `Telefono(ClienteID, NumeroTelefono)`

---

#### **Paso 4: Tratamiento de Entidades Débiles**
- **Entidades Débiles:** No pueden ser identificadas únicamente por su propio atributo.
  - Incluye la clave primaria de la entidad fuerte relacionada en la tabla de la entidad débil, junto con la clave parcial.

  **Ejemplo:**
  - Entidad débil: `Dependiente` (relacionada con `Empleado`).
  - Tabla: `Dependiente(DependienteID, Nombre, EmpleadoID (FK))`

---

#### **Paso 5: [[Normalización]]** 
- **Normalización:** Proceso de eliminación de redundancias y mejora de la integridad de la base de datos. Aplica las primeras formas normales (1FN, 2FN, 3FN) para evitar datos duplicados o dependencias ineficientes.

  - **1FN:** Asegura que cada campo contenga solo valores atómicos.
  - **2FN y 3FN:** Elimina dependencias funcionales parciales y transitivas, respectivamente.

---

### **3. Ejemplo Completo: De Diagrama ER a Tablas Relacionales**

- **Caso de Estudio:** Universidad (ER Diagram)
  - Entidades: `Estudiante`, `Profesor`, `Curso`
  - Relaciones: 
    - `Estudiante` - `Curso` (N:M)
    - `Profesor` - `Curso` (1:N)
  
- **Modelo Relacional:**
  - Tablas:
    1. `Estudiante(EstudianteID (PK), Nombre)`
    2. `Profesor(ProfesorID (PK), Nombre)`
    3. `Curso(CursoID (PK), Titulo, ProfesorID (FK))`
    4. `Inscripcion(EstudianteID (FK), CursoID (FK))`

---

### **4. Herramientas para el Modelado**
- Herramientas que facilitan la creación y conversión de diagramas ER al modelo relacional:
  - **MySQL Workbench**
  - **ER/Studio**
  - **Lucidchart**

---

### **Recursos Adicionales**
- **Libros:**
  - *Database System Concepts* de Abraham Silberschatz.
  - *Fundamentals of Database Systems* de Ramez Elmasri y Shamkant B. Navathe.

- **Enlaces útiles:**
  - Documentación oficial de MySQL Workbench: https://dev.mysql.com/doc/workbench/en/
  - Ejemplos de diagramas ER: https://www.lucidchart.com/pages/er-diagram-template

