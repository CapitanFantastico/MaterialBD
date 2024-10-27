
# Taller de Álgebra Relacional

## Objetivos

- Comprender y aplicar las operaciones básicas y avanzadas del álgebra relacional.
- Desarrollar habilidades para transformar requisitos del mundo real en consultas de álgebra relacional.

## Instrucciones

Para cada uno de los siguientes ejercicios, se deberá escribir la expresión de álgebra relacional que cumpla con el requerimiento dado. Se proporcionan dos esquemas de relaciones como punto de partida para los ejercicios:

1. **Empleados**(`IDEmpleado`, `Nombre`, `Apellido`, `DepartamentoID`, `Salario`)
2. **Departamentos**(`DepartamentoID`, `NombreDepartamento`, `Ubicacion`)

### Ejercicio 1: Selección y Proyección

1. Obtener los nombres de todos los empleados del departamento 3.
2. Listar los ID y nombres de los departamentos ubicados en "Madrid".

### Ejercicio 2: Unión, Intersección y Diferencia

Suponiendo una segunda tabla de empleados **EmpleadosTemporal** con la misma estructura que **Empleados**:

3. Listar todos los empleados (por `IDEmpleado`) que están tanto en **Empleados** como en **EmpleadosTemporal**.
4. Encontrar los empleados que están en **Empleados** pero no en **EmpleadosTemporal**.

### Ejercicio 3: Producto Cartesiano y Join

5. Realizar un join entre **Empleados** y **Departamentos** para obtener una lista de empleados con el nombre de su departamento.
6. Mostrar los nombres de los empleados junto con los nombres de sus departamentos utilizando un **Join Natural**.

### Ejercicio 4: Theta Join y EquiJoin

7. Listar los empleados que tienen un salario mayor a 3000 junto con su departamento, utilizando Theta Join.
8. Realizar un EquiJoin entre **Empleados** y **Departamentos** basado en `DepartamentoID`.

### Ejercicio 5: División

Suponiendo una relación **Proyectos**(`ProyectoID`, `NombreProyecto`) y **EmpleadoProyecto**(`IDEmpleado`, `ProyectoID`):

9. Encontrar los empleados que trabajan en todos los proyectos.

### Ejercicio 6: Funciones de Agregación y Agrupamiento

10. Calcular el salario promedio por departamento.

### Ejercicio 7: Left, Right y Full Outer Join

11. Realizar un Left Outer Join entre **Empleados** y **Departamentos** para listar a todos los empleados, incluyendo aquellos sin departamento asignado.
12. Realizar un Right Outer Join entre **Empleados** y **Departamentos** para listar todos los departamentos, incluyendo aquellos sin empleados asignados.
13. Realizar un Full Outer Join entre **Empleados** y **Departamentos** para mostrar todos los empleados y todos los departamentos, independientemente de si hay una correspondencia entre ellos o no.
