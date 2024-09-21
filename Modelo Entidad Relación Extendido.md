.
- https://manuel.cillero.es/doc/metodologia/metrica-3/tecnicas/modelo-entidad-relacion-extendido/

# Modelo Entidad/Relación Extendido

Se trata de una técnica cuyo objetivo es la representación y definición de todos los datos que se introducen, almacenan, transforman y producen dentro de un sistema de información, sin tener en cuenta las necesidades de la tecnología existente, ni otras restricciones.

Dado que el modelo de datos es un medio para comunicar el significado de los datos, las relaciones entre ellos y las reglas de negocio de un sistema de información, una organización puede obtener numerosos beneficios de la aplicación de esta técnica, pues la definición de los datos y la manera en que éstos operan son compartidos por todos los usuarios.

Las ventajas de realizar un modelo de datos son, entre otras:

- Comprensión de los datos de una organización y del funcionamiento de la organización.
- Obtención de estructuras de datos independientes del entorno físico.
- Control de los posibles errores desde el principio, o al menos, darse cuenta de las deficiencias lo antes posible.
- Mejora del mantenimiento.

Aunque la estructura de datos puede ser cambiante y dinámica, normalmente es mucho más estable que la estructura de procesos. Como resultado, una estructura de datos estable e integrada proporciona datos consistentes que puedan ser fácilmente accesibles según las necesidades de los usuarios, de manera que, aunque se produzcan cambios organizativos, los datos permanecerán estables.

Este diagrama se centra en los datos, independientemente del procesamiento que los transforma y sin entrar en consideraciones de eficiencia. Por ello, es independiente del entorno físico y debe ser una fiel representación del sistema de información objeto del estudio, proporcionando a los usuarios toda la información que necesiten y en la forma en que la necesiten.

### Descripción

El modelo entidad/relación extendido describe con un alto nivel de abstracción la distribución de datos almacenados en un sistema. Existen dos elementos principales: las entidades y las relaciones. Las extensiones al modelo básico añaden además los atributos de las entidades y la jerarquía entre éstas. Estas extensiones tienen como finalidad aportar al modelo una mayor capacidad expresiva.

Los elementos fundamentales del modelo son los siguientes:

## Entidad

Es aquel objeto, real o abstracto, acerca del cual se desea almacenar información en la base de datos. La estructura genérica de un conjunto de entidades con las mismas características se denomina tipo de entidad.

Existen dos clases de entidades: regulares, que tienen existencia por sí mismas, y débiles cuya existencia depende de otra entidad. Las entidades deben cumplir las siguientes tres reglas:

- Tienen que tener existencia propia.
- Cada ocurrencia de un tipo de entidad debe poder distinguirse de las demás.
- Todas las ocurrencias de un tipo de entidad deben tener los mismos atributos.

## Relación

Es una asociación o correspondencia existente entre una o varias entidades. La relación puede ser regular, si asocia tipos de entidad regulares, o débil, si asocia un tipo de entidad débil con un tipo de entidad regular. Dentro de las relaciones débiles se distinguen la **dependencia en existencia** y la **dependencia en identificación**.

Se dice que la dependencia es en existencia cuando las ocurrencias de un tipo de entidad débil no pueden existir sin la ocurrencia de la entidad regular de la que dependen. Se dice que la dependencia es en identificación cuando, además de lo anterior, las ocurrencias del tipo de entidad débil no se pueden identificar sólo mediante sus propios atributos, sino que se les tiene que añadir el identificador de la ocurrencia de la entidad regular de la cual dependen.

Además, se dice que una relación es **exclusiva** cuando la existencia de una relación entre dos tipos de entidades implica la no existencia de las otras relaciones.

Una relación se caracteriza por:

- **Nombre**: que lo distingue unívocamente del resto de relaciones del modelo.
- **Tipo de correspondencia**: es el número máximo de ocurrencias de cada tipo de entidad que pueden intervenir en una ocurrencia de la relación que se está tratando.  
    Conceptualmente se pueden identificar tres clases de relaciones:
    - Relaciones 1:1: Cada ocurrencia de una entidad se relaciona con una y sólo una ocurrencia de la otra entidad.
    - Relaciones 1:N: Cada ocurrencia de una entidad puede estar relacionada con cero, una o varias ocurrencias de la otra entidad.
    - Relaciones M:N: Cada ocurrencia de una entidad puede estar relacionada con cero, una o varias ocurrencias de la otra entidad y cada ocurrencia de la otra entidad puede corresponder a cero, una o varias ocurrencias de la primera.
- **Cardinalidad**: representa la participación en la relación de cada una de las entidades afectadas, es decir, el número máximo y mínimo de ocurrencias de un tipo de entidad que pueden estar interrelacionadas con una ocurrencia de otro tipo de entidad. La cardinalidad máxima coincide con el tipo de correspondencia.

Según la cardinalidad, una relación es obligatoria, cuando para toda ocurrencia de un tipo de entidad existe al menos una ocurrencia del tipo de entidad asociado, y es opcional cuando, para toda ocurrencia de un tipo de entidad, puede existir o no una o varias ocurrencias del tipo de entidad asociado.

## Dominio

Es un conjunto nominado de valores homogéneos. El dominio tiene existencia propia con independencia de cualquier entidad, relación o atributo.

## Atributo

Es una propiedad o característica de un tipo de entidad. Se trata de la unidad básica de información que sirve para identificar o describir la entidad. Un atributo se define sobre un dominio. Cada tipo de entidad ha de tener un conjunto mínimo de atributos que identifiquen unívocamente cada ocurrencia del tipo de entidad. Este atributo o atributos se denomina identificador principal. Se pueden definir restricciones sobre los atributos, según las cuales un atributo puede ser:

- Univaluado, atributo que sólo puede tomar un valor para todas y cada una de las ocurrencias del tipo de entidad al que pertenece.
- Obligatorio, atributo que tiene que tomar al menos un valor para todas y cada una de las ocurrencias del tipo de entidad al que pertenece.
![[Separador.png]]
==Además de estos elementos, existen extensiones del modelo entidad/relación que incorporan determinados conceptos o mecanismos de abstracción para facilitar la representación de ciertas estructuras del mundo real:==

- La **generalización**, permite abstraer un tipo de entidad de nivel superior (supertipo) a partir de varios tipos de entidad (subtipos); en estos casos los atributos comunes y relaciones de los subtipos se asignan al supertipo. Se pueden generalizar por ejemplo los tipos _profesor_ y _estudiante_ obteniendo el supertipo _persona_.

- La **especialización** es la operación inversa a la generalización, en ella un supertipo se descompone en uno o varios subtipos, los cuales heredan todos los atributos y relaciones del supertipo, además de tener los suyos propios. Un ejemplo es el caso del tipo _empleado_, del que se pueden obtener los subtipos _secretaria_, _técnico_ e _ingeniero_.

- **Categorización**. Se denomina categoría al subtipo que aparece como resultado de la unión de varios tipos de entidad. En este caso, hay varios supertipos y un sólo subtipo. Si por ejemplo se tienen los tipos _persona_ y _compañía_ y es necesario establecer una relación con _vehículo_, se puede crear _propietario_ como un subtipo unión de los dos primeros.


La existencia de supertipos y subtipos, en uno o varios niveles, da lugar a una **jerarquía**, que permitirá representar una restricción del mundo real.

Una vez construido el modelo entidad/relación, hay que analizar si se presentan redundancias. Para poder asegurar su existencia se deben estudiar con mucho detenimiento las cardinalidades mínimas de las entidades, así como la semántica de las relaciones.

Los atributos redundantes, los que se derivan de otros elementos mediante algún calculo, deben ser eliminados del modelo entidad/relación o marcarse como redundantes.

Igualmente, las relaciones redundantes deben eliminarse del modelo, comprobando que al eliminarlas sigue siendo posible el paso, tanto en un sentido como en el inverso, entre las dos entidades que unían.

![[Separador.png]]

### Notación

## Entidad  
La representación gráfica de un tipo de entidad regular es un rectángulo etiquetado con el nombre del tipo de entidad. Un tipo de entidad débil se representa con dos rectángulos concéntricos con su nombre en el interior.

![[Pasted image 20240910195740.png]]

## Relación

Se representa por un rombo unido a las entidades relacionadas por dos líneas rectas a los lados. El tipo de correspondencia se representa gráficamente con una etiqueta `1:1`, `1:N` o `M:N`, cerca de alguno de los vértices del rombo, o bien situando cada número o letra cerca de la entidad correspondiente, para mayor claridad.

![[Pasted image 20240910195845.png]]

La representación gráfica de las cardinalidades se realiza mediante una etiqueta del tipo `(0,1)`, `(1,1)`, `(0,n)` o `(1,n)`, que se coloca en el extremo de la entidad que corresponda. Si se representan las cardinalidades, la representación del tipo de correspondencia es redundante.

![[Pasted image 20240910200111.png]]

## Atributo

Un atributo se representa mediante una elipse, con su nombre dentro, conectada por una línea al tipo de entidad o relación.

En lugar de una elipse puede utilizarse un círculo con el nombre dentro, o un círculo más pequeño con el nombre del atributo a un lado. También pueden representarse en una lista asociada a la entidad. El identificador aparece con el nombre marcado o subrayado, o bien con su círculo en negro.

![[Pasted image 20240910200147.png]]

## Exclusividad

En la representación de las relaciones exclusivas se incluye un arco sobre las líneas que conectan el tipo de entidad a los dos o más tipos de relación.

![[Pasted image 20240910200222.png]]
![[Separador.png]]
## Lo nuevo para Entidad Relación Extendido

- Implementa el concepto de orientación a objetos para facilitar la modelación 
	- objeto=entidad 
	- clase=tipo entidad 
	- atributos 
	- jerarquía especialización/generalización
	- herencia=es_un
- Los métodos no se modelan


### Implementación de estructuras que representan las relaciones entre entidades (es_un, pertenece, unión):

#### Jerarquía: clase - subclase

![[Pasted image 20240919141922.png]]
- Se representa con un arco que indica que una subclase es un subconjunto (no propio) de una clase
	- X1 ⊆ X
- Se reconoce como una relación "es_un",
	- X1 es_un X
- X1 hereda todos los atributos de X
- X1 hereda todas las relaciones de X


#### Jerarquía de especialización / generalización

![[Pasted image 20240919141824.png]]

- Especialización: 
	- De la superclase X, derivo algunas subclases X1, X2, ..., Xn
	- La especialización se realiza mediante un proceso de abstracción del diseño de tipo top-down
- Generalización: 
	- De las clases X1, X2, ..., Xn derivo la superclase X 
	- X1 ⊆ X, X2 ⊆ X, ... Xn ⊆ X.
	- La generalización se realiza mediante un proceso de abstracción del diseño de tipo botton-up
- Todas las [[Restricciones implícitas]] de una jerarquía clase - subclase, se cumplen para cada una de las subclases X1, X2, ..., Xn respecto a la superclase X
- X es la clase general
- Xi son las clases especializadas
- X, Xi son entidades
- No se representa estrictamente como un árbol con el nodo arriba
- [[Restricciones implícitas]] o inherentes
	- Restricción de participación
		- Total: X con línea doble
			- (∀x | x ∈ X) : x ∈ X1 ∪ X2 ∪ ... ∪ Xn
		- Parcial: X con línea simple 
			- (∃x | x ∈ X) : x ∉ X1 ∪ X2 ∪ ... ∪ Xn
	- Restricción de membresía
		- d: Disjunta: 
			- (∀x | x ∈ X) : x ∈ Xi, x ∉ Xj → i ≠ j
		- o: Solapada: 
			- (∃x | x ∈ X) : x ∈ Xi, x ∈ Xj, i ≠ j
	- Restricción de definición
		- Arbitraria o definida por el usuario
			- No se diagrama
		- Por atributo
			- Existe un conjunto de atributos que me permite identificar en qué subclase va una instancia determinada
			- En el arco de la superclase va la lista de atributos
			- En el arco de cada subclase va la lista de los valores correspondientes 
		- Por condición
			- En cada arco que va a las subclases va la condición lógica que define qué instancias van en la subclase


#### Categorización

![[Pasted image 20240919142045.png]]

- La relación "es_un" va en sentido contrario: X es un X1 o un X2, ..., o un Xn
- X es una subclase de X1 ∪ X2 ∪ ... ∪ Xn
- X ⊆ X1 ∪ X1 ∪ ... ∪ Xn 
	- Puede darse el caso donde algunas instancias de Xi no estén en X y eso depende del universo del discurso
	- Ejemplo: X: propietarios de vehículos, X1: personas, X2: empresas.  Si el universo del discurso lo permite, pueden haber personas o empresas dentro de la instancia de base de datos que no posean un vehículo
	- [[Restricciones implícitas]] o inherentes
		- Restricción de participación
			- Total: X con línea doble.  el arco de flecha roma a X determina el sentido
				- (∀x | x ∈ X1 ∪ X2 ∪ ... ∪ Xn) : x ∈ X
			- Parcial: X con línea simple 
				- (∃x | x ∈ X1 ∪ X2 ∪ ... ∪ Xn) : x ∉ X

- Aparece el concepto de herencia selectiva
- Una instancia x de X puede heredar de X1, o de X2, ..., o de Xn, pero no de todas (la unión es disjunta generalmente, pero podría darse un caso particular donde un x de X herede de Xi y de Xj con i ≠ j)

---
### Otras notaciones

#### Jerarquía de especialización / generalización

La representación de las jerarquías se realiza mediante un triángulo invertido, con la base paralela al rectángulo que representa el supertipo y conectando a éste y a los subtipos. Si la división en subtipos viene determinada en función de los valores de un atributo discriminante, éste se representará asociado al triángulo que representa la relación.


![[Pasted image 20240910200335.png]]

En el triángulo se representará: con una letra **d** el hecho de que los subtipos sean disjuntos, con un círculo o una **O** si los subtipos pueden solaparse.  La presencia de una jerarquía total se representa con una doble línea entre el supertipo y el triángulo.

![[Pasted image 20240910200357.png]]


#### Categorización

La representación de las categorización se realiza mediante un triángulo, con la base paralela a la entidad que representa la unión de las otras clases.

![[Pasted image 20240919114350.png]]

En el triángulo se escribe una **U** que indica la unión por categorías. 


![[Pasted image 20240919112537.png]]

##### Ejemplo

Modelo entidad-relación extendido para un sistema de gestión de técnicos y su asignación a proyectos dentro de una empresa u organización.

Como se aprecia en el diagrama, TÉCNICO es un subtipo de EMPLEADO, generado por especialización, pues era necesario para establecer la relación **Trabaja en** PROYECTO, ya que no todos los empleados de la empresa, como los administrativos, son susceptibles de trabajar en un proyecto. La entidad TÉCNICO tendrá los atributos de EMPLEADO más el atributo **nivel**.

![[Pasted image 20240910200559.png]]

Los tipos de correspondencia son `1:N` entre DEPARTAMENTO y EMPLEADO, pues un departamento tiene 1 o varios empleados. Entre TÉCNICO y PROYECTO es `M:N`, pues un técnico puede trabajar en 1 o varios proyectos, y en un proyecto trabajan 1 o varios técnicos.

Por otro lado, se han incluido atributos que caracterizan la relación **Trabaja en**, como son **fecha de asignación** y **fecha de cese**, ya que un técnico no siempre estará trabajando en un proyecto, sino en determinado periodo. 
![[Separador.png]] 
- Ver [[Traducción del MER extendido al MR]] 
- Ver [[Relación entre generalización y especialización]] 
- Ver https://gestionbasesdatos.readthedocs.io/es/latest/Tema2/Teoria.html
- https://www.youtube.com/watch?v=1RMWhRtB_NQ&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=23
- https://www.youtube.com/watch?v=gk6HAEqRv8A&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=22&pp=iAQB
- https://www.youtube.com/watch?v=ptG0XTDrh_w&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=21&pp=iAQB
- https://www.youtube.com/watch?v=ev85Bkmyr6A&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=19&pp=iAQB
- https://www.youtube.com/watch?v=0j8InH4ybo4&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=20&pp=iAQB
- https://www.youtube.com/watch?v=PLbLmIKSgmY&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=18&pp=iAQB
- https://www.youtube.com/watch?v=ZDUGduw3vyc&list=PLeepWRg_899scidnv1P0hM9jJIiv-6kti&index=17&pp=iAQB
![[Separador.png]]
