.
- Es una [[Superclave]] tal que ningún subconjunto propio de sus atributos sea por sí mismo una superclave. 

- Por tanto, una clave candidata debe ser un identificador ==mínimo==. 

- Si en una tabla de estudiantes(CodigoEstudiante, CedulaEstudiante, Nombre, Apellido, Especialidad) tenemos la superclave {CodigoEstudiante, Apellido} no es una clave candidata porque contiene un subconjunto propio, { CodigoEstudiante }, que es una superclave. Sin embargo, CodigoEstudiante por sí mismo es una clave candidata. 

- Si a ningún par de estudiantes se le permite tener la misma combinación de valores para nombre y especialidad, la combinación {Apellido, Especialidad} también sería una clave candidata. 

- Por tanto, se ve que una relación puede tener varias claves candidatas. 

- Se usará el término **llave compuesta** para referir una llave que consista en más de un atributo.