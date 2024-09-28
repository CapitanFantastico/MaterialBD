.
- Es un atributo o conjunto de atributos que identifica de manera única una entidad. 

- En una tabla, una superclave es cualquier columna o conjunto de columnas cuyos valores se pueden usar para distinguir una fila de otra. 

- En consecuencia, una superclave es cualquier identificador único.

- Dado que una superclave identifica de manera única a cada entidad, determina funcionalmente a todos los atributos de una relación. 

- Para una tabla Estudiante, {IDEstudiante} es una superclave. Al igual que la combinación de {IDEstudiante, Apellido}. De hecho, {IDEstudiante, cualquier otro atributo} es una superclave para esta relación. De hecho, cualquier conjunto de atributos que contengan una superclave también es una superclave. 

- Sin embargo, una superclave puede contener atributos adicionales que no son necesarios para exclusividad, y el interés está en encontrar superclaves que no contengan tales atributos adicionales.

### Ejemplo de Superclave:

Consideremos una tabla `Estudiantes` con los siguientes campos: 

- `ID_Estudiante` (un identificador único para cada estudiante)
- `Nombre`
- `Apellido`
- `Fecha_de_Nacimiento`
- `Numero_de_Telefono`

En este caso:
- El campo `ID_Estudiante` por sí solo podría ser una clave primaria porque identifica unívocamente a cada estudiante. Por lo tanto, también es una superclave.
- La combinación de `Nombre`, `Apellido`, y `Fecha_de_Nacimiento` también podría funcionar como una superclave, suponiendo que no haya dos estudiantes con el mismo nombre, apellido y fecha de nacimiento. Sin embargo, esta combinación puede contener más información de la necesaria para identificar unívocamente a un estudiante si `ID_Estudiante` ya cumple esa función por sí solo.
- La combinación de `ID_Estudiante` y `Numero_de_Telefono` también es una superclave, dado que incluye la clave primaria (`ID_Estudiante`), pero añade información adicional (el `Numero_de_Telefono`) que no es necesaria para la identificación única, manteniendo la propiedad de unicidad.

- Ver [[Diferencia entre clave primaria y superclave]] 
---

### **Ejemplo del Cálculo de una Superclave Compuesta por Varias Claves Candidatas**

Una superclave es cualquier conjunto de atributos que pueda identificar de manera única una tupla en una relación. Puede estar compuesta por una o más claves candidatas, y puede incluir atributos adicionales que no sean necesarios para la identificación única pero que aún forman parte de la superclave.

Para ilustrar este concepto, usaremos un ejemplo cotidiano relacionado con la gestión de estudiantes en una universidad.

### **Caso Cotidiano: Base de Datos de Estudiantes**

Supongamos que tenemos una tabla `ESTUDIANTES` con los siguientes atributos:

- **Matrícula**: Número único de registro de cada estudiante.
- **Número de Identificación (ID)**: Documento de identificación personal (como DNI o cédula).
- **Correo Electrónico**: Email institucional del estudiante.
- **Nombre Completo**: Nombre y apellidos del estudiante.
- **Teléfono**: Número de contacto del estudiante.

### Dependencias Funcionales del Sistema:

1. **Matrícula → Nombre Completo, ID, Correo Electrónico, Teléfono**
2. **ID → Nombre Completo, Matrícula, Correo Electrónico, Teléfono**
3. **Correo Electrónico → Matrícula, Nombre Completo, ID, Teléfono**

### **Identificación de Claves Candidatas:**
En este sistema, las siguientes son claves candidatas porque cada una puede identificar de manera única a un estudiante:

1. **Matrícula**
2. **ID**
3. **Correo Electrónico**

### **Objetivo: Calcular una Superclave Compuesta por Varias Claves Candidatas**

Queremos construir una superclave usando una combinación de las claves candidatas mencionadas.

### **Paso a Paso del Cálculo de la Superclave:**

1. **Definición del Conjunto Inicial de Atributos (Superclave Candidata):**
   - Comienza por combinar varias claves candidatas en un solo conjunto.
   - Ejemplo: `{Matrícula, ID, Correo Electrónico}`.

2. **Verificación de Identificación Única:**
   - Verifica si la combinación de estos atributos identifica de manera única a cada estudiante en la tabla.
   - En este caso, `{Matrícula, ID, Correo Electrónico}` es una superclave, ya que cada clave candidata individualmente identifica de manera única a un estudiante. La combinación de estas asegura aún más la unicidad.

3. **Incluye Atributos Adicionales:**
   - Puedes agregar más atributos a esta superclave para formar otras superclaves. Por ejemplo:
     - `{Matrícula, ID, Correo Electrónico, Nombre Completo}`
     - `{Matrícula, ID, Correo Electrónico, Teléfono}`

4. **Comprobación de Redundancia:**
   - Es importante notar que, aunque cada clave candidata individual ya identifica de manera única a un estudiante, la combinación sigue siendo válida como superclave, aunque contenga redundancias.

### **Resultado Final:**
- Una superclave podría ser `{Matrícula, ID, Correo Electrónico}`. Esta combinación incluye tres claves candidatas diferentes.
- Otras posibles superclaves añadiendo atributos adicionales serían `{Matrícula, ID, Correo Electrónico, Nombre Completo}` o `{Matrícula, ID, Correo Electrónico, Teléfono}`.

### **Interpretación del Ejemplo:**
- Aunque cada clave candidata (Matrícula, ID, Correo Electrónico) puede identificar de manera única a un estudiante por sí sola, la combinación de estas crea una superclave que aún asegura la identificación única.
- La superclave puede contener múltiples claves candidatas y otros atributos adicionales, siempre que mantenga la capacidad de identificación única de los registros.

### **Importancia en la Normalización:**

Identificar superclaves y entender su composición es crucial para el diseño de esquemas de bases de datos y para asegurarse de que las tablas estén correctamente estructuradas, evitando redundancias y asegurando la integridad de los datos. En este ejemplo, conocer las superclaves ayuda a visualizar todas las combinaciones posibles que garantizan la unicidad de los registros en la tabla de estudiantes.