.
- Es el conjunto de claves que son [[Clave candidata]] más la [[Clave primaria]] 

- En el ejemplo, CodigoEstudiante puede ser la clave primaria y CedulaEstudiante una clave alterna. Estos dos atributos se determinan de modo funcional uno a otro, y todos los atributos son ==funcionalmente dependientes== de cada uno de ellos. 

- Cuando se toma una decisión acerca de cuál clave candidata usar como la clave primaria, es importante considerar cuál elección es una mejor representación del mundo real en el que funciona la empresa. 

- Se elige CodigoEstudiante en lugar de CedulaEstudiante porque, dado que la universidad asigna valores CodigoEstudiante, siempre puede estar seguro de tener dicho valor para cada estudiante. Es posible que no se tenga el número de cédula de cada estudiante. Por ejemplo, los estudiantes extranjeros pueden no tener números de cédula. Aunque no se establece de manera explícita en la definición

- Una importante característica de una clave primaria es que ninguno de sus atributos puede tener valores nulos. Si en las claves se permiten valores nulos, sería incapaz de separar los registros, dado que dos registros con valores nulos en el mismo campo de clave pueden ser indistinguibles. 

- Para claves candidatas se especificará que sus valores también son únicos en la base de datos. Esto ayuda a asegurar la calidad de los datos pues se sabe que los valores duplicados serían incorrectos para estos ítems. También es deseable reforzar la regla de “no nulos” para claves candidatas, siempre que pueda asegurar la disponibilidad del valor de la clave candidata.

- Ver [[Diferencia entre clave prima y clave primaria]] 