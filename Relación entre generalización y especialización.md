.
- https://barcelonageeks.com/diferencia-entre-generalizacion-y-especializacion-en-dbms/

# Diferencia entre generalización y especialización en DBMS

Posted on [julio 5, 2022](https://barcelonageeks.com/diferencia-entre-generalizacion-y-especializacion-en-dbms/)by [Rudeus Greyrat](https://barcelonageeks.com/author/rudeus_greyrat/)

La generalización y la especialización son el diagrama de relación de entidad mejorada (diagrama EER)

**1. Generalización:**  
Funciona según el principio del enfoque de abajo hacia arriba. En la generalización, las funciones de nivel inferior se combinan para formar funciones de nivel superior que se denominan entidades. Este proceso se repite más para hacer entidades de nivel avanzado.

En el proceso de Generalización, las propiedades se extraen de entidades particulares y, por lo tanto, podemos crear una entidad generalizada. Podemos resumir el proceso de Generalización ya que combina subclases para formar una superclase.

**Ejemplo de Generalización –**  
Considere dos entidades Estudiante y Paciente. Estas dos entidades tendrán algunas características propias. Por ejemplo, la entidad Student tendrá Roll_No, Name y Mob_No, mientras que el paciente tendrá las características PId, Name y Mob_No. Ahora, en este ejemplo, el Nombre y Mob_No tanto del Estudiante como del Paciente se pueden combinar como una Persona para formar una entidad de nivel superior y este proceso se denomina Proceso de Generalización.

![[Pasted image 20240917082648.png]]

**2. Especialización:**  
Podemos decir que la Especialización es lo opuesto a la Generalización. En Especialización, las cosas se dividen en cosas más pequeñas para simplificarlo aún más. También podemos decir que en la Especialización una entidad en particular se divide en subentidades y se hace en base a sus características. También en la Especialización tiene lugar la Herencia.

**Ejemplo de especialización:**  
considere una cuenta de entidad. Este tendrá algunos atributos, considérelos Acc_No y Balance. La entidad de la cuenta puede tener otros atributos como Current_Acc y Savings_Acc. Ahora Current_Acc puede tener Acc_No, Balance y Transactions mientras Savings_Acc puede tener Acc_No, Balance y Interest_Rate de ahora en adelante podemos decir que las entidades especializadas heredan características de entidad de nivel superior.

![[Pasted image 20240917082716.png]]

Después de aplicar la generalización y la especialización, la estructura de las figuras resultantes es la misma.

**Diferencia entre generalización y especialización:**

|GENERALIZACIÓN|ESPECIALIZACIÓN|
|---|---|
|La generalización funciona en el enfoque Bottom-Up.|La especialización funciona en un enfoque de arriba hacia abajo.|
|En Generalización, el tamaño del esquema se reduce.|En Especialización, se aumenta el tamaño del esquema.|
|La generalización se aplica normalmente a un grupo de entidades.|Podemos aplicar la Especialización a una sola entidad.|
|La generalización se puede definir como un proceso de creación de agrupaciones a partir de varios conjuntos de entidades.|La especialización se puede definir como el proceso de creación de subagrupaciones dentro de un conjunto de entidades|
|En el proceso de generalización, lo que realmente sucede es que se necesita la unión de dos o más conjuntos de entidades de nivel inferior para producir conjuntos de entidades de nivel superior.|La especialización es inversa a la generalización. La especialización es un proceso de tomar un subconjunto de un conjunto de entidades de nivel superior para formar un conjunto de entidades de nivel inferior.|
|El proceso de generalización comienza con la cantidad de conjuntos de entidades y crea una entidad de alto nivel con la ayuda de algunas características comunes.|El proceso de especialización comienza con un solo conjunto de entidades y crea un conjunto de entidades diferente mediante el uso de algunas características diferentes.|
|En la Generalización, las diferencias y similitudes entre las entidades inferiores se ignoran para formar una entidad superior.|En Especialización, una entidad superior se divide para formar entidades inferiores.|
|No hay herencia en la Generalización.|Hay herencia en la Especialización.|

---

- https://www.dataprix.com/es/bases-datos-master-software-libre-uoc/221-generalizacionespecializacion


# Generalizacion/especializacion

[![Profile picture for user Dataprix](https://www.dataprix.com/files/styles/thumbnail/public/pictures/logo_dataprix_screen_96.jpg?itok=c8z6bxQH)](https://www.dataprix.com/es/user/dataprix)

 By [Dataprix](https://www.dataprix.com/es/user/dataprix "Ver perfil del usuario.") on 29 Septiembre, 2009 - 10:44

En algunos casos, hay ocurrencias de una entidad que tienen características propias específicas que nos interesa modelizar. Por ejemplo, puede ocurrir que se quiera tener constancia de qué coche de la empresa tienen asignado los empleados que son directivos; también que, de los empleados técnicos, interese tener una interrelación con una entidad _proyecto_ que indique en qué proyectos trabajan y se desee registrar su titulación. Finalmente, que convenga conocer la antigüedad de los empleados administrativos. Asímismo, habrá algunas características comunes a todos los empleados: todos se identifican por un DNI, tienen un nombre, un apellido, una dirección y un número de teléfono.

Explain

`La generalización/especialización permite reflejar el hecho de que hay una entidad general, que denominamos entidad superclase, que se puede especializar en entidades subclase:   a) La entidad superclase nos permite modelizar las características comunes de la entidad vista de una forma genérica.   b) Las entidades subclase nos permiten modelizar las características propias de sus especializaciones.   Es necesario que se cumpla que toda ocurrencia de una entidad subclase sea también una ocurrencia de su entidad superclase.`

Denotamos la generalización/especialización con una flecha que parte de las entidades subclase y que se dirige a la entidad superclase.

Ejemplo de entidades superclase y subclase

En la figura siguiente están representadas la entidad superclase, que corresponde al empleado del ejemplo anterior, y las entidades subclase, que corresponden al directivo, al técnico y al administrativo del mismo ejemplo.

![[Pasted image 20240917082920.png]]

En la generalización/especialización, las características (atributos o interrelaciones) de la entidad superclase se propagan hacia las entidades subclase. Es lo que se denomina herencia de propiedades.

En el diseño de una generalización/especialización, se puede seguir uno de los dos procesos siguientes:

1)  Puede ocurrir que el diseñador primero identifique la necesidad de la entidad superclase y, posteriormente, reconozca las características específicas que hacen necesarias las entidades subclase. En estos casos se dice que ha seguido un proceso de especialización.

2)  La alternativa es que el diseñador modelice en primer lugar las entidades subclase y, después, se dé cuenta de sus características comunes e identifique la en- tidad superclase. Entonces se dice que ha seguido un proceso de generalización.

La generalización/especialización puede ser de dos tipos:

|   |
|---|
|Nuestro ejemplo de los empleados...|
|...corresponde a una generalización/especialización disjunta porque ningun empleado puede ser más de un tipo. Se denota con la etiqueta D.|

a)  Disjunta. En este caso no puede suceder que una misma ocurrencia apa- rezca en dos entidades subclase diferentes. Se denota gráficamente con la etiqueta D.

b)  Solapada. En este caso no tiene lugar la restricción anterior. Se denota grá- ficamente con la etiqueta S.

Además, una generalización/especialización también puede ser:

1)  Total. En este caso, toda ocurrencia de la entidad superclase debe pertenecer a alguna de las entidades subclase. Esto se denota con la etiqueta T.

2)  Parcial. En este caso no es necesario que se cumpla la condición anterior. Se denota con la etiqueta P.

La generalización/especialización de los empleados

La generalización/especialización de los empleados es total porque suponemos que todo empleado debe ser directivo, técnico o administrativo. Se denota con la etiqueta T.


![[Pasted image 20240917082953.png]]