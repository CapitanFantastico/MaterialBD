## Fuentes
- https://www.youtube.com/watch?v=vh0KMMsTGQ0 - 01
- https://www.youtube.com/watch?v=YbkzfKW8FhI&t=1264s - 02 Álgebra Relacional | Ejemplos 1 a 4 | Relax
- https://www.youtube.com/watch?v=K2epLH0tJuE - 03
- https://dbis-uibk.github.io/relax/ - Página para pruebas en línea
- https://jorgesanchez.net/manuales/viejos/abd/algebra1.pdf - Taller
- Elmasri, Ramez; Navathe, Shamkant, B. (2007). Fundamentos de sistemas de bases de datos (5a ed.). Madrid_ Pearson Educac ( PDFDrive ) - Libro en pdf
- https://www.youtube.com/watch?t=16&v=dgexA92PhlI&feature=youtu.be - Tutorial Relax
- https://www.ionos.es/digitalguide/hosting/cuestiones-tecnicas/sql-join/

- Ver [[Cálculo relacional]] 
- [[Operadores relacionales en SQL]] 
## Intro

Suponga que tiene dos tablas: 

- **EMPLEADOS**(<u>IDEmpleado</u>, NombreEmpleado, IDDepartamento)
- **DEPARTAMENTOS**(<u>IDDepartamento</u>, NombreDepartamento)

- Ver https://videlcloud.wordpress.com/2017/03/05/buenas-practicas-para-el-diseno-de-base-de-datos/
- Ver https://docs.aws.amazon.com/es_es/athena/latest/ug/tables-databases-columns-names.html

Ahora suponga que necesita mostrar la lista de nombres de los empleados que trabajan en el departamento Ventas

Ejercicio: 

- Haga un programa que muestre la información solicitada

Programa en Python que toma dos diccionarios, uno de Empleados con la información ID Empleado, Nombre Empleado y ID Departamento, y otro de Departamentos, con la información ID Departamento y Nombre Departamento, y muestre el Nombre de todos los Empleados que tengan como ID Departamento aquel Departamento cuyo Nombre Departamento sea igual a "Ventas" 

```
# Diccionario de Empleados con ID Empleado, Nombre Empleado, y ID Departamento
empleados = {
    1: {"Nombre": "Juan Pérez", "ID_Departamento": 101},
    2: {"Nombre": "Ana Gómez", "ID_Departamento": 102},
    3: {"Nombre": "Carlos Ruiz", "ID_Departamento": 101},
    4: {"Nombre": "María López", "ID_Departamento": 103},
}

# Diccionario de Departamentos con ID Departamento y Nombre Departamento
departamentos = {
    101: {"Nombre": "Ventas"},
    102: {"Nombre": "Marketing"},
    103: {"Nombre": "Desarrollo"},
}

# Buscar el ID del departamento llamado "Ventas"
id_departamento_ventas = None
for id_dep, dep_info in departamentos.items():
    if dep_info["Nombre"] == "Ventas":
        id_departamento_ventas = id_dep
        break

# Mostrar el nombre de los empleados que pertenecen al departamento de "Ventas"
if id_departamento_ventas is not None:
    print("Empleados en el departamento de Ventas:")
    for emp_id, emp_info in empleados.items():
        if emp_info["ID_Departamento"] == id_departamento_ventas:
            print(emp_info["Nombre"])
else:
    print("No se encontró el departamento 'Ventas'")

```

---

- Un ==modelo de datos== debe incluir un conjunto de ==operaciones== para manipular la base de datos junto con los conceptos necesarios para la definición de su ==estructura y restricciones==. El conjunto de operaciones básicas del modelo relacional es el álgebra relacional

- El álgebra relacional permite al usuario especificar las peticiones fundamentales de recuperación. El resultado de una recuperación es una nueva relación, la cual puede estar constituida por una o más relaciones. Por consiguiente, ==las operaciones de álgebra producen nuevas relaciones== que pueden ser manipuladas más adelante usando operaciones del mismo álgebra. 

- Una ==secuencia de operaciones== de álgebra relacional conforma una ==expresión== de álgebra relacional, cuyo resultado será también una nueva relación que representa el resultado de una ==consulta== a la base de datos (o una ==petición de recuperación==).

- Algunos de los conceptos del álgebra relacional se han incorporado al lenguaje estándar de consultas SQL para los RDBMS.

---
## Operaciones

![[Pasted image 20240313100605.png]]

![[Pasted image 20241024125337.png]]

| Operación        | Álgebra Relacional                       | SQL (PostgreSQL y MySQL)                          |
| ---------------- | ---------------------------------------- | ------------------------------------------------- |
| **Selección**    | σ<sub>condición</sub>(R)                 | `SELECT * FROM R WHERE condición;`                |
| **Proyección**   | π<sub>A1, A2, ..., An</sub>(R)           | `SELECT A1, A2, ..., An FROM R;`                  |
| **Renombrado**   | ρ<sub>S</sub>(R) / ρ<sub>A -> B</sub>(R) | `SELECT * FROM R AS S;` / `SELECT A AS B FROM R;` |
| **Unión**        | R1 ∪ R2                                  | `SELECT * FROM R1 UNION SELECT * FROM R2;`        |
| **Intersección** | R1 ∩ R2                                  | `SELECT * FROM R1 INTERSECT SELECT * FROM R2;`    |
| **Diferencia**   | R1 - R2                                  | `SELECT * FROM R1 EXCEPT SELECT * FROM R2;`       |
| **Producto**     | R1 x R2                                  | `SELECT * FROM R1, R2;`                           |
| **Join**         | R1 ⨝<sub>condición</sub> R2              | `SELECT * FROM R1 JOIN R2 ON condición;`          |
| **Join natural** | R1 * R2                                  | `SELECT * FROM R1 NATURAL JOIN R2;`               |
| **División**     | R1 ÷ R2                                  | `SELECT A1 FROM R1 WHERE NOT EXISTS (...);`       |


---
### SELECCIÓN (Sigma σ)

- Se emplea para seleccionar un subconjunto de las tuplas de una relación que satisfacen una condición de selección. 

- SELECCIÓN es una operación unaria, es decir, se aplica a una sola relación. Además, esta operación se aplica a cada tupla individualmente

- Es representada como:
			$\sigma$ $_{<condición de selección>}$ (R)

- Donde R es una relación o una expresión de álgebra relacional cuyo resultado es una relación

- Y `<condición de selección>` puede ser una cadena de condiciones donde se compara un atributo de la relación R con una constante o con otro atributo, ambos del mismo dominio, y donde pueden haber operadores lógicos 

- Los operadores `[ =, <, <=, >, >=, <> ]` se aplican a los atributos cuyos dominios son valores ordenados (ej. números, fechas),  en caso contrario, sólo pueden usarse los operadores `{=, ≠}`. 

- El ==grado de la relación== resultante es el mismo que el de la relación R (los mismos atributos) y la ==cardinalidad== es menor o igual que la cardinalidad de R.

- El ejemplo siguiente muestra la operación de selección de las ==tuplas== de EMPLEADOS donde IDDepartamento=4: 
			$\sigma$ $_{IDDepartamento=4}$ (EMPLEADOS)
			
- El ejemplo siguiente muestra la operación de selección de las tuplas de EMPLEADOS donde Salario>30000: 
		 $\sigma$ $_{Salario>30000}$ (EMPLEADOS)

- El ejemplo siguiente muestra la operación de selección de las tuplas de EMPLEADOS donde IDDepartamento = 4 y Salario > 25000, o IDDepartamento = 5 y Salario > 30000: 
		$\sigma$ <sub>(IDDepartamento=4 AND Salario>25000) OR (IDDepartamento=5 AND Salario>30000)</sub> (EMPLEADOS)

- Observe que la operación SELECCIÓN es conmutativa, es decir:
		$\sigma$$_{<condición1>}$($\sigma$$_{<condición2>}$(R)) = $\sigma$ $_{<condición2>}$($_{<condición1>}$(R))

- Por tanto, puede aplicarse una secuencia de SELECCIONES en cualquier orden. Además, siempre podemos combinar una **cascada** de operaciones **SELECCIÓN** en una sola a través de un (AND):
		$\sigma$ $_{<condición1>}$($\sigma$$_{<condición2>}$(. . .( $\sigma$$_{<condición>}$(R)) . . .)) 
	es igual a
		$\sigma$$_{<condición1> AND <condición2> AND . . . AND <condición>}$(R) 

- El ejemplo siguiente muestra diversas formas de selección de las tuplas de EMPLEADOS donde Salario > 2500 y Salario < 3000: 
		$\sigma$ $_{Salario>2500}$ ($\sigma$ $_{Salario<3000}$ (EMPLEADOS))
		$\sigma$ $_{Salario<3000}$ ($\sigma$ $_{Salario>2500}$ (EMPLEADOS))
		$\sigma$ $_{(Salario>2500 AND Salario>3000)}$ (EMPLEADOS)

### PROYECCIÓN (Pi π)

- Selecciona y muestra los atributos especificados de la relación R 

- Es representada como:
		$\pi$ $_{<lista de atributos>}$ (R)

- Donde R es una relación o una expresión de álgebra relacional cuyo resultado es una relación

- Y  ${<lista de atributos>}$ contiene la lista de atributos de la relación R que queremos seleccionar. 

- El ==grado== de la relación resultante es **menor o igual** al de la relación R (los atributos especificados en ${<lista de atributos>}$) y la ==cardinalidad== es **menor o igual** que la de la relación R.  😕

- Si la ${<listadeatributos>}$ sólo incluye atributos no clave de R, es posible que se dupliquen tuplas y la operación PROYECCIÓN ==elimina cualquier tupla duplicada==.. 

- El ejemplo siguiente selecciona y muestra Nombre, Apellido y Salario de la relación EMPLEADOS:
		$\pi$ $_{Nombre, Apellido, Salario}$ (EMPLEADOS)

- El ejemplo siguiente muestra la operación PROYECCIÓN del atributo Salario y no muestra duplicados:
		$\pi$ $_{Salario}$ (EMPLEADO)

- La eliminación de duplicados lleva implícito un proceso de ordenación para detectar esos registros repetidos y, por tanto, es más costoso en términos de procesamiento. 💡 

- Los resultados duplicados no están permitidos en el modelo relacional formal, pero sí lo esta en la práctica. 👈

	- Se deduce que:
			$\pi$ $_{<lista1>}$ ($\pi$ $_{<lista2>}$(R)) = $\pi$ $_{<lista1>}$ (R)

	 Siempre que:
		 ${<lista2>}$ contenga los atributos de ${<lista1>}$

	 De otro modo, la parte de la izquierda es una expresión incorrecta. 

### Secuencia de operaciones y RENAME (Rho ρ)

- Podemos escribir operaciones como una única expresión de álgebra relacional anidando dichas operaciones o aplicar una sola expresión una única vez y crear relaciones intermedias. 

- El ejemplo siguiente muestra la expresión para recuperar Nombre, Apellido y Salario de  la relación EMPLEADOS donde IDDepartamento=5

- Podemos escribir una expresión de álgebra relacional sencilla de la siguiente forma:
		$\pi$ $_{Nombre, Apellido1, Salario}$ ($\sigma$ $_{IDDepartamento=5}$ (EMPLEADOS))

- Alternativamente, podemos mostrar la secuencia de operaciones, dando un nombre a cada relación intermedia:
		EMPLEADOS5 ← $\sigma$ $_{IDDepartamento=5}$ (EMPLEADOS)
		RESULTADO ← $\pi$ $_{Nombre, Apellido, Salario}$ (EMPLEADOS5)

- Si es necesario renombrar los atributos de una relación resultante, enumeramos los nuevos nombres de atributos dentro de los paréntesis: 👈
		TEMP ← σ $_{IDDepartamento=5}$ (EMPLEADO)
		R<sub>(NuevoNombre, NuevoApellido, NuevoSalario)</sub> ← $\pi$ $_{Nombre, Apellido, Salario}$ (TEMP)

- Podemos definir la operación RENAME como un operador unario. Una operación RENAME aplicada a una relación R de grado n aparece denotada de cualquiera de estas tres formas:
		$\rho$ $_{S(B1, B2, ..., Bn)}$ (R) "Aquí se renombra la relación y los atributos"
		$\rho$ $_S$ (R)  "Aquí sólo se renombra la relación"
		$\rho$ $_{(B1, B2, ..., Bn)}$ (R) "Aquí sólo se renombran los atributos"
		
- ==Donde S es el nombre de la nueva relación y B1, B2, . . ., Bn son los de los nuevos nombres de atributos.==

- El ejemplo siguiente muestra cómo es posible renombrar los atributos de la relación ESTUDIANTES, renombrar la relación y renombrar ambos:

	ESTUDIANTES(IDEstudiante, NombreEstudiante, ApellidoEstudiante)
	ρ $_{(ID, Nombre, Apellido)}$ (ESTUDIANTES)
	ρ $_{PARTICIPANTES}$ (ESTUDIANTES)
	ρ $_{PARTICIPANTES (ID, Nombre, Apellido)}$ (ESTUDIANTES)

## Operaciones de álgebra relacional de la teoría de conjuntos

### UNION, INTERSECTION y MINUS

- Son operaciones binarias, es decir, se aplican a dos conjuntos (de tuplas)

- Las relaciones sobre las que se aplican estas tres operaciones deben tener "compatibilidad de unión".  

	R(A1, A2, . . . , An) y S(B1, B2, . . ., Bn) son de unión compatible si tienen el mismo grado n y si el dom(Ai) = dom(Bi) para 1 ≤ i ≤ n. 🔴

	Esto significa que ambas relaciones tienen el mismo número de atributos y que cada par correspondiente cuenta con el mismo dominio.

- UNION. El resultado de esta operación, especificada como R ∪ S, es una relación que incluye todas las tuplas que están tanto en R como en S o en ambas, R y S. Las tuplas duplicadas se eliminan.

- INTERSECTION. El resultado de esta operación, especificada como R ∩ S, es una relación que incluye todas las tuplas que están en R y en S.

- MINUS. El resultado de esta operación, especificada como R-S, es una relación que incluye todas las tuplas que están en R pero no en S.

- Las operaciones UNION e INTERSECTION son conmutativas, esto es,
		R ∪ S = S ∪ R 
		R ∩ S = S ∩ R

- Observe que la INTERSECCIÓN puede expresarse en términos de unión y diferencia de conjuntos del siguiente modo:
		R ∩ S = (R ∪ S) – (R - S) – (S - R)


- El ejemplo siguiente muestra la expresión para seleccionar los atributos Nombre y Apellido de las relaciones EMPLEADOS y CONTRATISTAS
		$\pi$ $_{Nombre, Apellido}$ ($\sigma$ $_{IDDepartamento=5}$ **EMPLEADOS**) ∪ $\pi$ $_{Nombre, Apellido}$ ($\sigma$ $_{IDDepartamento=5}$ **CONTRATISTAS**) 

- Si quiero incluir el IDEmpleado y el IDContratista, debo renombrar uno de los dos atributos
		$\pi$ $_{IDEmpleado, Nombre, Apellido}$ ($\sigma$ $_{IDDepartamento=5}$ (EMPLEADOS)) ∪ 
		$\rho$ $_{(IDEmpleado, Nombre, Apellido)}$ ($\pi$ $_{IDContratista, Nombre, Apellido}$ ($\sigma$ $_{IDDepartamento=5}$ (CONTRATISTAS))) 

- Si hubieran dos relaciones distintas con igual número de atributos y con los mismos nombres, se podría seleccionar las tuplas de las dos relaciones con la siguiente expresión:
		RELACION1 ∪ RELACION2

- Es de aclarar que los resultados del operador UNION también devuelve tuplas no duplicadas, en caso que las hubiera.

### CROSS PRODUCT/CROSS JOIN (Producto cartesiano X)

- Es una relación binaria

- No es necesario que las relaciones en las que se aplica sean una unión compatible.

- En general, el resultado de R(A1, A2, . . . , An ) X S (B1, B2, . . . , Bm ) es una relación Q con un grado de n + m atributos Q(A1, A2, . . . , An, B1, B2, . . . , Bm ), en este orden. La relación resultante Q tiene una tupla por cada combinación de éstas (una para R y otra para S). Por tanto, si R tiene n$_R$ tuplas (indicado como |R| = n$_R$ ), y S cuenta con n$_S$ tuplas, R X S tendrá n$_R$ ∗ n$_S$ tuplas.

- La operación aplicada es, por sí misma, absurda. Es útil cuando va seguida por una selección que correlacione los valores de los atributos procedentes de las relaciones componentes. 🔴

- Podría resultar útil para crear una combinatoria de elementos:  
		**PROTEINAS** x **CARBOHIDRATOS** x **VERDURAS**
		
- O armar parejas para una competencia:
		**PROFESORES** x **ALUMNOS**


## Operaciones relacionales binarias: JOIN y DIVISION


### JOIN (⨝) 

- La operación JOIN se emplea para combinar tuplas de dos relaciones con atributos asociados. 

- Y es representada como:
	
	R ⨝$_{<condición de conexión>}$S

- Supongamos que queremos recuperar el nombre del director de cada departamento. Para ello, necesitamos combinar las tuplas de DEPARTAMENTOS (IDDepartamento, NombreDepartamento, IDDirector) y EMPLEADOS (IDEmpleado, NombreEmpleado) :

	**EMPLEADOS** ⨝`<IDEmpleado=IDDirector>` **DEPARTAMENTOS**

- Esta operación crea un conjunto de resultados en el que cada tupla (fila) es el resultado de combinar las tuplas de EMPLEADOS con las de DEPARTAMENTOS donde el criterio de unión (usualmente una ==llave foránea== que coincide con una ==llave primaria==) se cumple.  

- En el resultado sólo aparecen las combinaciones de tuplas que satisfacen la condición de conexión

- Una condición general de conexión tiene la forma:

	<condición> AND <condición> AND . . . AND <condición>

- Un JOIN con una condición de conexión de este tipo recibe el nombre de THETA JOIN ($\theta$ Join). 🔴

Si quisieramos consultar todas las posibles parejas de empleados donde la fecha de ingreso del primero sea menor que la fecha de ingreso del segundo y trabajen en el mismo departamento, podríamos realizar la siguiente operación:

**EMPLEADOS** ⨝`(IDDepartamento = IDDepartamento AND FechaIngreso < FechaIngreso)` **EMPLEADOS**


- El uso más habitual de JOIN supone el uso de condiciones de conexión sólo con comparaciones de igualdad, en cuyo caso recibe el nombre de EQUIJOIN

- ==En el resultado de un EQUIJOIN siempre tenemos uno o más pares de atributos que cuentan con valores idénticos en cada tupla.  Ya que uno de estos valores idénticos es innecesario, se creó una nueva operación llamada NATURAL JOIN (identificada por ∗) para deshacerse del segundo atributo superfluo en una condición EQUIJOIN.==

- La definición estándar de esta operación precisa que los dos atributos de conexión tengan el mismo nombre en ambas relaciones. Si éste no es el caso, se aplica en primer lugar una operación de renombrado.

	**EMPLEADOS** `*` ρ <sub>(IDDepartamento, NombreDepartamento)</sub>  (π <sub>ID, Nombre</sub> **DEPARTAMENTOS**)

- Cómo sería para obtener la lista de empleados, el nombre del departamento y el nombre del director del departamento?


### Un conjunto completo de operaciones de álgebra relacional

- Todas las operaciones de álgebra relacional {σ, $\pi$, ∪, -, x} conforman un conjunto completo, es decir, que cualquiera de las operaciones originales puede expresarse como una secuencia de operaciones de este conjunto 🔴

### DIVISION

- El operador de división en álgebra relacional, aunque no es tan intuitivo como otros operadores como la selección o la unión, es bastante útil en ciertos contextos específicos, especialmente cuando queremos encontrar tuplas en una relación que se relacionan con todas las tuplas en otra relación.

- Supongamos que tenemos dos relaciones:

	A(X, Y), donde X e Y son conjuntos de atributos.
	B(Y), donde B contiene solo un subconjunto de los atributos de A, específicamente aquellos atributos en Y.

- La división de A por B, denotada como A ÷ B, nos da una nueva relación que contiene todas las tuplas de X (es decir, las partes de las tuplas de A que no están en B) tales que para cada tupla en B, existe una tupla en A que coincide con ella.

- Imaginemos que A representa una relación de "Proyectos" con atributos (EmpleadoID, ProyectoID) indicando qué empleado trabaja en qué proyecto. B representa una relación de "ProyectosEspecíficos" con un único atributo (ProyectoID) listando solo proyectos específicos.

- Si queremos encontrar los empleados que trabajan en todos los proyectos listados en B, usaríamos el operador de división.

- El resultado de A ÷ B sería una relación con el atributo (EmpleadoID), listando solo aquellos empleados que trabajan en todos los proyectos mencionados en B.

- Supongamos la siguiente instancia para A (Proyectos):

| EmpleadoID | ProyectoID |
|------------|------------|
|     1      |     a      |
|     1      |     b      |
|     2      |     a      |
|     3      |     a      |
|     3      |     b      |

- Y B (ProyectosEspecíficos):

| ProyectoID |
|------------|
|     a      |
|     b      |

- La división A ÷ B nos daría los EmpleadoID de empleados que trabajan en todos los proyectos mencionados en B:

| EmpleadoID |
|------------|
|     1      |
|     3      |

- Esto se debe a que solo los empleados 1 y 3 trabajan en ambos proyectos a y b.

- El operador de división es particularmente útil en consultas que implican frases como "para todos" o "cada uno", permitiéndonos realizar consultas que de otra manera requerirían lógica más compleja para implementar.

- La DIVISIÓN R ÷ S puede expresarse como una secuencia de operaciones ($\pi$, X , -)  del siguiente modo:

	T1 ← $\pi$ <sub>γ</sub> (R)
	T2 ← $\pi$ <sub>γ</sub> ((S x T1) - R)
	T ← T1 – T2

Donde γ es el subconjunto de atributos comunes entre R y S

## Operaciones relacionales adicionales

### Proyección generalizada

- Permite la inclusión de funciones de atributos en la lista de proyección

- Considere la relación:
	EMPLEADO (IDEmpleado, Sueldo, Deducción, Antigüedad)

- Un informe podría necesitar mostrar:

	SalarioNeto = Sueldo - Deducción,
	Bonificaciones = 2000 ∗ Antigüedad 
	Impuestos = 0,25 ∗ Sueldo

- De este modo, puede usarse una proyección generalizada combinada con una operación de renombrado de la siguiente forma:

	ρ <sub>(IDEmpleado, SalarioNeto, Bonificaciones, Impuestos)</sub> (π <sub>IDEmpleado, Sueldo – Deducción, 2000 ∗ Antiguedad, 0.25 ∗ Sueldo</sub> (EMPLEADO)).


### Funciones de agregación y agrupamiento

- Las más comunes son Suma (SUM), Media (AVG), Máximo (MAX) y Mínimo (MIN). La función CONTAR (COUNT) se emplea para contar tuplas o valores.

- Supone realizar la agrupación de las tuplas de una relación por el valor de uno de sus atributos y la aplicación posterior de una función de agregación independiente a cada grupo.

- El ejemplo siguiente muestra la recuperación de cada Departamento, el número de empleados del mismo y la media de salarios, renombrando los atributos resultantes tal y como se especifica:

ρ <sub>R(IDDepartamento, NumEmpleados, MediaSueldos)</sub>($_{IDDepartamento}$ λ<sub>COUNT(IDEmpleado), AVG(Salario)</sub> (EMPLEADOS))

 - Siendo $\lambda$ la función de agrupamiento

- Si no se especifican atributos de agrupamiento, las funciones se aplican a todas las tuplas de la relación, por lo que obtendremos como resultado una única tupla. 🔴

### OUTER JOIN (Join externo)

- Hasta ahora, todo Join al que nos habíamos referido, lo podemos identificar también como INNER JOIN (Join interno)

- Operaciones que son esenciales para consultas que necesitan incluir filas de una o ambas tablas relacionadas, incluso cuando no hay una coincidencia entre ellas, las vamos a referir como OUTER JOIN (Join externo). 

- A diferencia del INNER JOIN, que solo devuelve las filas que tienen coincidencias en ambas tablas, las operaciones de OUTER JOIN pueden retornar todas las filas de una tabla, más las filas coincidentes de la otra tabla (si las hay), ==llenando con valores nulos las columnas de la tabla donde no hay coincidencia==.

- Pueden ser de los siguientes tipos: LEFT OUTER JOIN, RIGHT OUTER JOIN, y FULL OUTER JOIN. 

- Estos conceptos pueden ser simulados combinando varias operaciones básicas del álgebra relacional, como el JOIN natural (`*`), la diferencia (−), y la unión (∪), junto con operaciones de proyección (π) y selección (σ).

### LEFT OUTER JOIN

- El **LEFT OUTER JOIN** de **EMPLEADOS** con **DEPARTAMENTOS** sobre el campo **IDDepartamento** devolverá todos los empleados y la información del departamento al que pertenecen. Si algún empleado no pertenece a un departamento que se encuentre en la tabla Departamentos, aún así se mostrará, con NULL en los campos del departamento.

	**EMPLEADOS** ⨝<sub>L IEMPLEADOS.DDepartamento = DEPARTAMENTOS.IDDepartamento</sub> **DEPARTAMENTOS**


### RIGHT OUTER JOIN

- El **RIGHT OUTER JOIN** de **EMPLEADOS** con **DEPARTAMENTOS** sobre el campo **IDDepartamento** devolverá todos los departamentos y los empleados que pertenecen a ellos. Si hay departamentos sin empleados asignados, estos se mostrarán con NULL en los campos del empleado.

	**EMPLEADOS** ⨝<sub>R EMPLEADOS.IDDepartamento = DEPARTAMENTOS.IDDepartamento</sub> **DEPARTAMENTOS**

### FULL OUTER JOIN

- El **FULL OUTER JOIN** de **EMPLEADOS** con **DEPARTAMENTOS** sobre el campo **IDDepartamento** devolverá todos los empleados y todos los departamentos. Si un empleado no pertenece a un departamento presente en la tabla Departamentos, o si un departamento no tiene empleados asignados, estos se mostrarán con NULL en los campos correspondientes.

	**EMPLEADOS** ⨝<sub>F EMPLEADOS.IDDepartamento = DEPARTAMENTOS.IDDepartamento</sub> **DEPARTAMENTOS**

![[Pasted image 20240313162216.png]]

- Ver [[Historia del álgebra relacional]] 
- Ver [[Taller de Álgebra Relacional]] 


---
## Notas

- Ver [[Símbolos]] 
- [[Relax]] 
