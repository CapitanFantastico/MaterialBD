.
Los axiomas de Armstrong son reglas que nos permiten inferir todas las dependencias funcionales posibles o lógicamente implicadas a partir de un conjunto dado de dependencias funcionales.

Sean A, B, C y D subconjuntos de atributos de una relación R. Los siguientes axiomas se sostienen (note que aquí AC significa la unión del conjunto A y el conjunto C):

### **Reflexividad**. 

Si B es un subconjunto de A, entonces A → B. Esto también implica que A → A siempre se sostiene. Las dependencias funcionales de este tipo se llaman dependencias funcionales triviales.

**Ejemplo:**  

Supongamos que tenemos una tabla 

**Estudiante**(**ID_Estudiante**, Nombre, Apellido) 

donde **ID_Estudiante** es la clave primaria.   Podemos decir que 

**{ID_Estudiante, Nombre} → ID_Estudiante** 

porque 

**ID_Estudiante** es un subconjunto de **{ID_Estudiante, Nombre}**. 

Esto significa que si conocemos el ID y el nombre de un estudiante, podemos determinar su ID (lo cual es trivialmente cierto).
   
### **Aumento**. 

Si A → B, entonces AC → BC.

**Ejemplo:**  

Si en una tabla 

**Profesor**(**ID_Profesor**, Nombre, Departamento) 

se sabe que 

**ID_Profesor → Nombre**, 

entonces también se puede inferir que 

**{ID_Profesor, Departamento} → {Nombre, Departamento}**. 

Es decir, si conocemos el **ID del profesor**, podemos determinar su **nombre**, y esto sigue siendo cierto si agregamos el **departamento** a ambos lados de la dependencia funcional.

### **Transitividad**: 

Si X → Y y Y → Z, entonces X → Z.

**Ejemplo:**  

Consideremos dos dependencias funcionales en una tabla 

**Curso**(ID_Curso, Nombre_Curso, ID_Profesor):

1. Cédula → Ciudad 
2. Ciudad → Departamento 

Aplicando la transitividad, podemos inferir que 

**Cédula → Departamento**. 


### Axiomas derivados

Las siguientes reglas se pueden derivar a partir de las tres anteriores

- **Unión**. Si A → B y A → C, entonces A → BC.

- **Aditividad**. Si A → B y X → Y, entonces AX → BY

- **Proyectividad o descomposición**. Si A → BC, entonces A → B y A → C.

- **Pseudotransitividad**. Si A → B y BC → D, entonces AC → D.


### Ejemplo Completo con los Tres Axiomas: Sistema de Reservas

**Supongamos las siguientes dependencias:**

1. **Sala → Capacidad** (una sala determina su capacidad).
2. **Capacidad** → Equipamiento (cada capacidad tiene un equipamiento estándar).
3. **Sala → Ubicación** (una sala está en un edificio específico).

**Aplicaciones de los Axiomas:**

1. **Reflexividad:** **Sala → Sala** (es obvio que la sala determina su propio nombre o información).
   
2. **Aumentación:** Si **Sala → Capacidad**, entonces **Sala y Fecha → Capacidad y Fecha** (añadiendo la fecha no cambia la relación).

3. **Transitividad:** De **Sala → Capacidad** y **Capacidad → Equipamiento**, podemos deducir **Sala → Equipamiento** (saber la sala nos dice directamente el equipamiento).



---
### Axiomas de Armstrong Explicados

Los **Axiomas de Armstrong** son un conjunto de reglas fundamentales que se utilizan para derivar todas las dependencias funcionales válidas en una base de datos relacional. Estos axiomas son esenciales para comprender la teoría de la normalización y ayudar a asegurar la integridad de los datos. Para hacerlos más comprensibles, los explicaremos a través de ejemplos cotidianos.

### 1. ¿Qué son los Axiomas de Armstrong?

Los Axiomas de Armstrong son tres reglas básicas que permiten derivar nuevas dependencias funcionales a partir de otras ya conocidas. Son herramientas fundamentales en el análisis de bases de datos y se utilizan para probar si un conjunto de dependencias funcionales es completo y consistente.

### Los Tres Axiomas de Armstrong:

1. **Axioma de Reflexividad**
2. **Axioma de Aumentación**
3. **Axioma de Transitividad**

Vamos a explorar cada uno de ellos con ejemplos de la vida diaria.

### 1. Axioma de Reflexividad

**Definición:** Si `Y` es un subconjunto de `X`, entonces `X → Y`. Esto significa que cualquier conjunto de atributos determina a sus propios subconjuntos.

**Ejemplo:**

Imagina que tienes una tarjeta de identificación que contiene tu nombre completo, fecha de nacimiento y número de documento.

- **Dependencia Reflexiva:** Si tienes la tarjeta (`{nombre, fecha de nacimiento, número de documento}`), entonces puedes saber tu nombre (`nombre`). Es obvio que poseyendo toda la información, puedes acceder a cualquier parte de ella.

- **Analogía:** Es como decir que, si tienes toda la lista de ingredientes de una receta, sabes los ingredientes específicos.

### 2. Axioma de Aumentación

**Definición:** Si `X → Y`, entonces `XZ → YZ` para cualquier conjunto `Z`. Esto implica que si una dependencia funcional es verdadera, puedes añadir el mismo conjunto de atributos a ambos lados sin cambiar la relación.

**Ejemplo:**

En una biblioteca, tienes la dependencia `ISBN → Título`. Es decir, el ISBN te da el título del libro.

- **Aplicando Aumentación:** Si tienes `ISBN → Título`, entonces `ISBN y Ubicación → Título y Ubicación`. Añadir más información a ambos lados no cambia la dependencia funcional.

- **Analogía:** Si al saber tu número de matrícula puedes saber tu nombre, entonces también al saber tu número de matrícula y tu universidad, puedes saber tu nombre y tu universidad.

### 3. Axioma de Transitividad

**Definición:** Si `X → Y` y `Y → Z`, entonces `X → Z`. Este axioma refleja una cadena de determinación a través de varios pasos.

**Ejemplo:**

En una empresa, si `Departamento → Gerente` (un departamento tiene un gerente) y `Gerente → Oficina` (cada gerente tiene una oficina), entonces podemos deducir que `Departamento → Oficina` (cada departamento tiene una oficina a través de su gerente).

- **Aplicación:** Si sabes que un gerente tiene una oficina específica y sabes a qué departamento pertenece ese gerente, puedes determinar qué oficina está asociada con cada departamento.

- **Analogía:** Es como decir que si "saber tu fecha de nacimiento" te dice tu "edad" y "saber tu edad" te dice tu "categoría de edad" (joven, adulto, etc.), entonces saber tu fecha de nacimiento puede determinar tu categoría de edad.

