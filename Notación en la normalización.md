.
### Notación

Una herramienta muy útil para visualizar las dependencias funcionales es el grafo o diagrama de dependencias funcionales, mediante el cual se representa un conjunto de atributos y las dependencias funcionales existentes entre ellos.

En el grafo aparecen los nombres de los atributos unidos por flechas, las cuales indican las dependencias funcionales completas que existen entre ellos, partiendo del implicante hacia el implicado. Cuando el implicante de una dependencia no es un único atributo, es decir, se trata de un implicante compuesto, los atributos que lo componen se encierran en un recuadro y la flecha parte de éste, no de cada atributo.

![[Pasted image 20240910195650.png]]

En la figura se presenta un ejemplo de cómo se visualizan las dependencias. Se puede observar que **COD_LIBRO** determina funcionalmente los atributos **TITULO** y **EDITORIAL**, como indica la correspondiente flecha; de forma análoga, **NUM_SOCIO** determina **NOMBRE**, **DOMICILIO** y **TEL** del socio (suponiendo que sólo se proporciona un teléfono); mientras que ambos atributos en conjunto **COD_LIBRO** y **NUM_SOCIO** (lo que se indica mediante el recuadro que los incluye) determinan **FEHA_PRESTAMO** y **FECHA_DEV**.

### Ejemplo

Sea una entidad **TÉCNICOS** de un grupo de empresas, con los siguientes atributos:

- cod_empresa
- cod_técnico
- nombre_técnico
- cod_categoría
- categoría
- nombre_empresa
- fecha_alta
- fecha_baja
- cod_conoc
- título_conoc
- área_conoc
- grado
- cod_proyecto
- nombre_proyecto
- f_inicio
- f_fin
- f_asignación
- f_cese
- cod_cliente
- nombre_cliente

La entidad TÉCNICOS tiene la clave principal compuesta por _cod_empresa_ y _cod_técnico_, ya que, al ser varias empresas, el código de técnico no será único, sino que puede coincidir con otros de otras empresas.

#### [[Primera forma normal]] (1FN)

Evidentemente no se cumple la primera forma normal, ya que un técnico tendrá más de un conocimiento (lenguajes, sistemas operativos, bases de datos, etc.), es decir habrá varios valores de _cod_conoc_, por lo que este atributo y los asociados a conocimientos no dependen funcionalmente de la clave principal.

Los atributos _cod_conoc_, _título_conoc_, _área_conoc_ y _grado_ identificados como no dependientes, formarán la nueva entidad **CONOCIMIENTOS** y desaparecerán de la entidad TÉCNICOS. La clave de la nueva entidad será _cod_conoc_ concatenada con _cod_empresa_ y _cod_técnico_.

Por otro lado, en este sistema un técnico puede trabajar en más de un proyecto a tiempo parcial, por lo que _cod_proyecto_ tampoco depende funcionalmente de la clave principal de TÉCNICOS.

Se obtiene entonces la entidad **PROYECTOS** con los atributos de los proyectos, y su clave compuesta de _cod_proyecto_ concatenada con _cod_empresa_ y _cod_técnico_ de la antigua entidad.

Esta situación se completará con dos tipos de relaciones: **Poseen**, cuyo tipo de correspondencia es 1:N entre **TÉCNICOS** y **CONOCIMIENTOS** y **Están asignados**, también del tipo M:N entre **TÉCNICOS** y **PROYECTOS**, tal y como muestra el diagrama siguiente.

![[Pasted image 20240910195623.png]]

Como se aprecia en la figura, se ha trasladado el atributo **grado** de la entidad **CONOCIMIENTOS** a la relación **Poseen**, pues es un atributo que determina la relación entre las dos entidades. También han sido trasladado los atributos que caracterizan la relación **Están asignados**, como son **f_asignación** y **f_cese**, ya que un técnico no siempre estará trabajando en un proyecto, sino en determinado periodo.

#### [[Segunda forma normal]] (2FN)

En la entidad **TÉCNICOS** se observa que el atributo **nombre_empresa** no tiene una dependencia funcional completa de la clave, sino que la tiene sólo de una parte de la misma: **cod_empresa**.

El atributo identificado formará parte de una nueva entidad, **EMPRESAS**, siendo eliminado de la antigua. La clave principal de la nueva entidad será **cod_empresa**.

Para representar la segunda forma normal en el modelo de datos, deberá añadirse un tipo de relación, **Se componen**, y el tipo de correspondencia 1:N.

![[Pasted image 20240910195554.png]]

#### [[Tercera forma normal]] (3FN)

En la entidad **TÉCNICOS** de la figura se puede observar que para un **cod_técnico** hay un único **cod_categoría**, es decir, el segundo depende funcionalmente del primero; para un **cod_categoría** hay una única **categoría**, es decir, que este atributo depende funcionalmente del **cod_categoría**; y por último, para un **cod_categoría** hay varios valores de **cod_técnico**. Así pues, la **categoría** depende transitivamente del **cod_técnico**, por lo que la entidad **TÉCNICOS** no está en 3FN.

Una vez identificado el atributo **categoría** que depende de otro atributo distinto de la clave, **cod_categoría**, se formará con él una nueva entidad y se quitará de la antigua. La clave principal de la nueva entidad será el atributo del cual depende **cod_categoría** y en la entidad antigua pasará a ser una clave ajena.

Del mismo modo, puede observarse que la entidad **PROYECTOS** tampoco está en 3FN, pues el **nombre_cliente** depende de **cod_cliente**, que no forma parte de la clave de la entidad.

![[Pasted image 20240910195522.png]]

Así pues, aparecen dos entidades nuevas en el modelo: **CATEGORÍAS** y **CLIENTES**, y sus respectivas relaciones y tipos de correspondencias: **Están clasificados** 1:N y **Tiene contratados** 1:N.