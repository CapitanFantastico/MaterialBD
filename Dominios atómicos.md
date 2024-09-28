.
- El modelo E-R permite que los conjuntos de entidades y los de relaciones tengan atributos con algún tipo de subestructura. 

- Concretamente, permite atributos ==multivalorados==, como teléfono, y atributos ==compuestos== (como el atributo dirección con los atributos componentes calle, carrera, numero, apartamento). 

- Cuando se crean tablas a partir de los diseños E-R que contienen ese tipo de atributos, se elimina esa subestructura. 

- Para los atributos compuestos, se deja que cada atributo componente sea un atributo de pleno derecho. 

- Para los atributos multivalorados, se crea una nueva relación con una tupla por cada elemento del conjunto multivalorado.

- En el modelo relacional se formaliza esta idea de que ==los atributos no tienen subestructuras==. 

- Un dominio es atómico si se considera que los elementos de ese dominio son ==unidades indivisibles==. 