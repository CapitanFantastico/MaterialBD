
Las operaciones del álgebra relacional tienen equivalentes en SQL, PostgreSQL y MySQL. A continuación, te muestro cómo implementar cada una de estas operaciones en SQL, que se aplica tanto a **PostgreSQL** como a **MySQL**.

### 1. **Selección (σ)**
   - **Álgebra relacional**:  
     \[
     \sigma_{\text{condición}}(R)
     \]
   - **SQL**:  
     ```sql
     SELECT * FROM R WHERE condición;
     ```
   - **Ejemplo**:
     ```sql
     SELECT * FROM empleados WHERE salario > 3000;
     ```

### 2. **Proyección (π)**
   - **Álgebra relacional**:  
     \[
     \pi_{A_1, A_2, ..., A_n}(R)
     \]
   - **SQL**:  
     ```sql
     SELECT A1, A2, ..., An FROM R;
     ```
   - **Ejemplo**:
     ```sql
     SELECT nombre, salario FROM empleados;
     ```

### 3. **Renombrado (ρ)**
   - **Álgebra relacional**:  
     \[
     \rho_{S}(R) \quad \text{o} \quad \rho_{A \rightarrow B}(R)
     \]
   - **SQL**:  
     Para renombrar una relación (tabla), generalmente se hace con un alias.
     ```sql
     SELECT * FROM R AS S;
     ```
     Para renombrar atributos:
     ```sql
     SELECT A AS B FROM R;
     ```
   - **Ejemplo**:
     ```sql
     SELECT nombre AS empleado_nombre FROM empleados;
     ```

### 4. **Unión ( ∪ )**
   - **Álgebra relacional**:  
     \[
     R_1 \cup R_2
     \]
   - **SQL**:  
     ```sql
     SELECT * FROM R1
     UNION
     SELECT * FROM R2;
     ```
   - **Ejemplo**:
     ```sql
     SELECT nombre FROM empleados_ventas
     UNION
     SELECT nombre FROM empleados_compras;
     ```
   - **Nota**: `UNION` en SQL elimina duplicados automáticamente. Si quieres mantener los duplicados, usa `UNION ALL`.

### 5. **Intersección ( ∩ )**
   - **Álgebra relacional**:  
     \[
     R_1 \cap R_2
     \]
   - **SQL**:  
     MySQL no tiene un operador `INTERSECT`, pero puedes simularlo con una combinación de `JOIN` o `IN`:
     ```sql
     SELECT * FROM R1
     INTERSECT
     SELECT * FROM R2;
     ```
     O bien, en MySQL:
     ```sql
     SELECT * FROM R1 WHERE columna IN (SELECT columna FROM R2);
     ```
   - **Ejemplo**:
     ```sql
     SELECT nombre FROM empleados_ventas
     INTERSECT
     SELECT nombre FROM empleados_compras;
     ```

### 6. **Diferencia ( − )**
   - **Álgebra relacional**:  
     \[
     R_1 - R_2
     \]
   - **SQL**:  
     SQL no tiene un operador directo para la diferencia, pero se puede implementar con `EXCEPT` (PostgreSQL) o usando `NOT IN`/`LEFT JOIN` en MySQL.
     ```sql
     SELECT * FROM R1
     EXCEPT
     SELECT * FROM R2;
     ```
     O en MySQL:
     ```sql
     SELECT * FROM R1 WHERE columna NOT IN (SELECT columna FROM R2);
     ```
   - **Ejemplo**:
     ```sql
     SELECT nombre FROM empleados_ventas
     EXCEPT
     SELECT nombre FROM empleados_compras;
     ```

### 7. **Producto cartesiano ( × )**
   - **Álgebra relacional**:  
     \[
     R_1 \times R_2
     \]
   - **SQL**:  
     ```sql
     SELECT * FROM R1, R2;
     ```
   - **Ejemplo**:
     ```sql
     SELECT * FROM empleados, proyectos;
     ```

### 8. **Join natural (⨝)**
   - **Álgebra relacional**:  
     \[
     R_1 \bowtie R_2
     \]
   - **SQL**:  
     ```sql
     SELECT * FROM R1
     NATURAL JOIN R2;
     ```
     El **NATURAL JOIN** combina las tuplas en las que los valores coinciden en los atributos comunes con el mismo nombre.
   - **Ejemplo**:
     ```sql
     SELECT * FROM empleados NATURAL JOIN departamentos;
     ```

### 9. **Theta Join (⨝θ)**
   - **Álgebra relacional**:  
     \[
     R_1 \bowtie_{\theta} R_2
     \]
   - **SQL**:  
     ```sql
     SELECT * FROM R1
     JOIN R2 ON condición;
     ```
   - **Ejemplo**:
     ```sql
     SELECT * FROM empleados e
     JOIN proyectos p ON e.salario > p.presupuesto;
     ```

### 10. **División (÷)**
   - **Álgebra relacional**:  
     \[
     R_1 ÷ R_2
     \]
   - **SQL**:  
     No existe una operación directa de división en SQL, pero puede implementarse mediante una combinación de `NOT EXISTS` o `GROUP BY` y `HAVING`. Aquí te muestro una forma básica:
     ```sql
     SELECT A1
     FROM R1
     WHERE NOT EXISTS (
         SELECT *
         FROM R2
         WHERE NOT EXISTS (
             SELECT *
             FROM R1
             WHERE R1.A1 = R2.A2 AND R1.A3 = R2.A3
         )
     );
     ```
   - **Ejemplo**:
     Si quieres encontrar empleados que trabajan en **todos los proyectos**:
     ```sql
     SELECT empleado_id
     FROM trabajos
     GROUP BY empleado_id
     HAVING COUNT(DISTINCT proyecto_id) = (SELECT COUNT(*) FROM proyectos);
     ```

### Resumen:

| Operación        | Álgebra Relacional                              | SQL (PostgreSQL y MySQL)                          |
| ---------------- | ----------------------------------------------- | ------------------------------------------------- |
| **Selección**    | \(\sigma_{\text{condición}}(R)\)                | `SELECT * FROM R WHERE condición;`                |
| **Proyección**   | \(\pi_{A_1, A_2, ..., A_n}(R)\)                 | `SELECT A1, A2, ..., An FROM R;`                  |
| **Renombrado**   | \(\rho_{S}(R)\) / \(\rho_{A \rightarrow B}(R)\) | `SELECT * FROM R AS S;` / `SELECT A AS B FROM R;` |
| **Unión**        | \(R_1 \cup R_2\)                                | `SELECT * FROM R1 UNION SELECT * FROM R2;`        |
| **Intersección** | \(R_1 \cap R_2\)                                | `SELECT * FROM R1 INTERSECT SELECT * FROM R2;`    |
| **Diferencia**   | \(R_1 - R_2\)                                   | `SELECT * FROM R1 EXCEPT SELECT * FROM R2;`       |
| **Producto**     | \(R_1 \times R_2\)                              | `SELECT * FROM R1, R2;`                           |
| **Join natural** | \(R_1 \bowtie R_2\)                             | `SELECT * FROM R1 NATURAL JOIN R2;`               |
| **Theta Join**   | \(R_1 \bowtie_{\theta} R_2\)                    | `SELECT * FROM R1 JOIN R2 ON condición;`          |
| **División**     | \(R_1 ÷ R_2\)                                   | `SELECT A1 FROM R1 WHERE NOT EXISTS (...);`       |

Aquí tienes la tabla formateada de manera que sea compatible con Obsidian. He reemplazado los símbolos del álgebra relacional por su descripción textual para que puedan visualizarse correctamente.

| Operación        | Álgebra Relacional                       | SQL (PostgreSQL y MySQL)                          |
| ---------------- | ---------------------------------------- | ------------------------------------------------- |
| **Selección**    | σ<sub>condición</sub>(R)                 | `SELECT * FROM R WHERE condición;`                |
| **Proyección**   | π<sub>A1, A2, ..., An</sub>(R)           | `SELECT A1, A2, ..., An FROM R;`                  |
| **Renombrado**   | ρ<sub>S</sub>(R) / ρ<sub>A -> B</sub>(R) | `SELECT * FROM R AS S;` / `SELECT A AS B FROM R;` |
| **Unión**        | R1 ∪ R2                                  | `SELECT * FROM R1 UNION SELECT * FROM R2;`        |
| **Intersección** | R1 ∩ R2                                  | `SELECT * FROM R1 INTERSECT SELECT * FROM R2;`    |
| **Diferencia**   | R1 - R2                                  | `SELECT * FROM R1 EXCEPT SELECT * FROM R2;`       |
| **Producto**     | R1 x R2                                  | `SELECT * FROM R1, R2;`                           |
| **Join natural** | R1 ⨝ R2                                  | `SELECT * FROM R1 NATURAL JOIN R2;`               |
| **Theta Join**   | R1 ⨝<sub>θ</sub> R2                      | `SELECT * FROM R1 JOIN R2 ON condición;`          |
| **División**     | R1 ÷ R2                                  | `SELECT A1 FROM R1 WHERE NOT EXISTS (...);`       |

Este formato debería copiarse y pegarse correctamente en Obsidian.