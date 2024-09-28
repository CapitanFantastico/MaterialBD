.
La **clave prima** y la **clave primaria** son conceptos relacionados con la identificación de registros en una base de datos relacional, pero tienen significados y roles específicos que a menudo se confunden. A continuación, te explico las diferencias y sus características:

### **Clave Prima**

1. **Definición**: Una **clave prima** es cualquier clave candidata en una relación. Es un conjunto de uno o más atributos que pueden identificar de manera única a cada registro en una tabla.
   
2. **Características**:
   - Una tabla puede tener múltiples claves primas.
   - Cada clave prima es única y no permite valores nulos.
   - Se utiliza para identificar posibles claves que puedan ser usadas como clave primaria.

3. **Ejemplos**:
   - Supongamos una tabla `Estudiantes` con los atributos `ID_Estudiante`, `DNI` (Documento Nacional de Identidad) y `Email`. En este caso, tanto `ID_Estudiante`, `DNI`, y `Email` pueden servir para identificar de manera única a un estudiante. Por lo tanto, todas son **claves primas**.

4. **Selección de la Clave Primaria**: Una de las claves primas se selecciona como la clave primaria. El resto son candidatas pero no seleccionadas como claves primarias, conocidas como **claves alternativas**.

### **Clave Primaria**

1. **Definición**: La **clave primaria** es una clave candidata seleccionada específicamente para identificar de manera única a cada registro de una tabla.

2. **Características**:
   - Solo puede haber **una clave primaria** por tabla.
   - Debe ser única y no puede contener valores nulos.
   - Se utiliza como la clave principal para la referencia en otras tablas, especialmente cuando se establecen relaciones entre tablas.

3. **Propósito**:
   - Garantiza la integridad de los datos al asegurar que cada registro es único.
   - Se utiliza para la indexación y mejora del rendimiento de la búsqueda de datos.

4. **Ejemplo**:
   - En la tabla `Estudiantes`, si se selecciona `ID_Estudiante` como la clave primaria, entonces `DNI` y `Email` seguirán siendo claves primas, pero no clave primaria.

### **Diferencias Clave**

| Característica         | Clave Prima                                 | Clave Primaria                                |
|------------------------|---------------------------------------------|-----------------------------------------------|
| **Número**             | Puede haber varias claves primas.           | Solo puede haber una clave primaria por tabla.|
| **Uso**                | Conjunto de claves candidatas.              | Clave seleccionada para identificar registros.|
| **Selección**          | No necesariamente utilizada para referencia.| Seleccionada de entre las claves primas.      |
| **Valores Nulos**      | No permite valores nulos.                   | No permite valores nulos.                     |
| **Propósito**          | Identificar candidatos para clave primaria. | Identificar de manera única los registros.    |

### **Relación entre Clave Prima y Clave Primaria**

- Todas las claves primarias son claves primas, pero no todas las claves primas se convierten en la clave primaria.
- La clave primaria se elige entre las claves primas con base en criterios como simplicidad, facilidad de uso y estabilidad de los datos.

