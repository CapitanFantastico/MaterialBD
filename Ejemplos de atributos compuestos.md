.
Un ejemplo de un atributo compuesto de **tres niveles** podría ser el **Nombre Completo**, que incluye subcomponentes que a su vez también se pueden desglosar en otros elementos.

### Ejemplo: Atributo Compuesto "Nombre Completo"

1. **Nombre Completo**
   - **Primer Nombre**
   - **Apellidos**
     - **Apellido Paterno**
     - **Apellido Materno**
   - **Prefijo**
   - **Sufijo**

La representación en un árbol de tres niveles sería la siguiente:

```
Nombre Completo
│
├── Primer Nombre
├── Apellidos
│   ├── Apellido Paterno
│   └── Apellido Materno
├── Prefijo
└── Sufijo
```

En este caso, el atributo **Apellidos** es un subcomponente que se desglosa en otros dos subcomponentes: **Apellido Paterno** y **Apellido Materno**, lo que agrega un tercer nivel a la estructura.