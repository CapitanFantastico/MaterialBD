.
- [[Anomalías de la base de datos]] <

==La normalización requiere tener un uso claro de la semántica del modelo.== ==Examinar simplemente una instancia no es suficiente==, porque una instancia no proporciona suficiente información acerca de todos los posibles valores o combinaciones de valores para atributos de relación.

Aquí no se utilizará la ==normalización== como una técnica de diseño de bases de datos, sino como una ==etapa posterior== a la correspondencia entre el esquema conceptual y el esquema lógico, que elimine las dependencias no deseadas entre atributos.

La teoría de la normalización tiene por objetivo la eliminación de dependencias entre atributos que originen **anomalías** en las operaciones de la base datos, y proporcionar una estructura más regular para la representación de las tablas, constituyendo el soporte para el diseño de bases de datos relacionales.

Como resultado de la aplicación de esta técnica se obtiene un modelo lógico de datos normalizado.

Se dice que una relación está en una determinada forma normal si satisface un cierto conjunto de restricciones sobre los atributos. Cuanto más restricciones existan, menor será el número de relaciones que las satisfagan, así, por ejemplo, una relación en tercera forma normal estará también en segunda y en primera forma normal.

Antes de definir las distintas formas normales se explican, muy brevemente, algunos conceptos necesarios para su comprensión.

- [[Dominios atómicos]] 
- [[Tipos de clave]] <
- [[Dependencias]] <

[[Formas normales]] <
[[Notación en la normalización]] < 
[[Ejemplo de normalización]] 
[[Desnormalización]] 
[[Taller de Normalización de Bases de Datos Relacionales]] 


- [[Otros conceptos en normalización]]
- [[Algoritmo de normalización BCNF]] 


