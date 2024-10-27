
En álgebra relacional, existen varias operaciones fundamentales que se utilizan para manipular relaciones. Cada una de estas operaciones tiene un **símbolo** específico, y además, las mismas operaciones pueden expresarse en **cálculo relacional** (ya sea cálculo relacional de tuplas o de dominios). A continuación te muestro las principales operaciones y sus correspondientes expresiones.

### 1. **Selección (σ)**
   - **Álgebra relacional**: Selecciona las tuplas que satisfacen una condición.
     \[
     \sigma_{\text{condición}}(R)
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid R(t) \land \text{condición}(t) \}
     \]
     Esto significa: selecciona todas las tuplas `t` en la relación `R` que cumplan la condición dada.

### 2. **Proyección (π)**
   - **Álgebra relacional**: Extrae un subconjunto de los atributos de una relación.
     \[
     \pi_{A_1, A_2, ..., A_n}(R)
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t[A_1, A_2, ..., A_n] \mid R(t) \}
     \]
     Esto significa: selecciona los atributos `A1, A2, ..., An` de las tuplas `t` en la relación `R`.

### 3. **Renombrado (ρ)**
   - **Álgebra relacional**: Cambia el nombre de una relación o de sus atributos.
     \[
     \rho_{S}(R) \quad \text{o} \quad \rho_{A \rightarrow B}(R)
     \]
   - **Cálculo relacional**: No existe una notación explícita para el renombrado en cálculo relacional, ya que las variables de tupla pueden cambiarse de nombre directamente.

### 4. **Unión ( ∪ )**
   - **Álgebra relacional**: Combina las tuplas de dos relaciones, eliminando duplicados.
     \[
     R_1 \cup R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid R_1(t) \lor R_2(t) \}
     \]
     Esto significa: selecciona las tuplas que están en `R1` o en `R2`.

### 5. **Intersección ( ∩ )**
   - **Álgebra relacional**: Obtiene las tuplas comunes a ambas relaciones.
     \[
     R_1 \cap R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid R_1(t) \land R_2(t) \}
     \]
     Esto significa: selecciona las tuplas que están tanto en `R1` como en `R2`.

### 6. **Diferencia ( − )**
   - **Álgebra relacional**: Obtiene las tuplas que están en una relación pero no en la otra.
     \[
     R_1 - R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid R_1(t) \land \neg R_2(t) \}
     \]
     Esto significa: selecciona las tuplas que están en `R1` pero no en `R2`.

### 7. **Producto cartesiano ( × )**
   - **Álgebra relacional**: Combina todas las tuplas de dos relaciones, formando el producto cartesiano.
     \[
     R_1 \times R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid \exists t_1 \exists t_2 (R_1(t_1) \land R_2(t_2) \land t = t_1 \cup t_2) \}
     \]
     Esto significa: selecciona todas las combinaciones de tuplas de `R1` y `R2`.

### 8. **Join (Unión natural) (⨝)**
   - **Álgebra relacional**: Combina las tuplas de dos relaciones que coinciden en atributos comunes.
     \[
     R_1 \bowtie R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid \exists t_1 \exists t_2 (R_1(t_1) \land R_2(t_2) \land t_1.A = t_2.A \land t = t_1 \cup t_2) \}
     \]
     Esto significa: selecciona todas las combinaciones de tuplas de `R1` y `R2` donde los atributos comunes coinciden.

### 9. **Theta Join (⨝θ)**
   - **Álgebra relacional**: Combina las tuplas de dos relaciones según una condición arbitraria (θ).
     \[
     R_1 \bowtie_{\theta} R_2
     \]
   - **Cálculo relacional** (de tuplas):
     \[
     \{ t \mid \exists t_1 \exists t_2 (R_1(t_1) \land R_2(t_2) \land \theta(t_1, t_2) \land t = t_1 \cup t_2) \}
     \]
     Esto significa: selecciona todas las combinaciones de tuplas de `R1` y `R2` que satisfacen la condición `θ`.

### 10. **División (÷)**
   - **Álgebra relacional**: Retorna las tuplas de una relación que están asociadas con todas las tuplas de otra relación.
     \[
     R_1 ÷ R_2
     \]
   - **Cálculo relacional** (de tuplas):
     Aunque no tiene una traducción directa en cálculo relacional, la división puede expresarse de manera equivalente usando cuantificadores:
     \[
     \{ t_1 \mid R_1(t_1, t_2) \land \forall t_2 (R_2(t_2) \rightarrow R_1(t_1, t_2)) \}
     \]
     Esto significa: selecciona las tuplas `t1` de `R1` que están relacionadas con **todas** las tuplas de `R2`.

### Resumen de símbolos del álgebra relacional:
- **Selección**: σ
- **Proyección**: π
- **Renombrado**: ρ
- **Unión**: ∪
- **Intersección**: ∩
- **Diferencia**: −
- **Producto cartesiano**: ×
- **Join natural**: ⨝
- **Theta join**: ⨝θ
- **División**: ÷

Estas operaciones son las herramientas fundamentales para construir consultas en álgebra relacional, y el cálculo relacional permite expresar consultas declarativas usando fórmulas lógicas.

