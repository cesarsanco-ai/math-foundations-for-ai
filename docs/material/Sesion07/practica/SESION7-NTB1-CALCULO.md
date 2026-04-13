---
layout: default
---
# Sesion 7: Ejercicios de Autovalores y Autovectores

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Autovalores de matriz diagonal

**Enunciado (contexto IA):** Para $A=\text{diag}(4,1,0.5)$ encuentra autovalores.

**Solución paso a paso:**

1) En diagonal, autovalores son entradas diagonales.
2) $\lambda=(4,1,0.5)$.
3) Indican factor de estiramiento por dirección.
4) IA: estabilidad de dinámica lineal.

### Ejercicio 2: Autovector asociado

**Enunciado (contexto IA):** Para $A=\text{diag}(4,1,0.5)$ y $\lambda=4$, da un autovector.

**Solución paso a paso:**

1) Dirección eje 1: $(1,0,0)^T$.
2) $A v=(4,0,0)=4v$.
3) Cualquier múltiplo también sirve.
4) Subespacio propio de dimensión 1.

### Ejercicio 3: Polinomio característico

**Enunciado (contexto IA):** Para $A=\begin{pmatrix}2&1\\0&3\end{pmatrix}$, calcula $p(\lambda)$.

**Solución paso a paso:**

1) $p(\lambda)=\det(A-\lambda I)$.
2) $\det\begin{pmatrix}2-\lambda&1\\0&3-\lambda\end{pmatrix}=(2-\lambda)(3-\lambda)$.
3) Raíces: 2 y 3.
4) Matriz triangular: autovalores en diagonal.

### Ejercicio 4: Suma y producto

**Enunciado (contexto IA):** Si autovalores son 5 y -2, halla traza y determinante.

**Solución paso a paso:**

1) Traza = suma = 3.
2) Determinante = producto = -10.
3) Verificación rápida de cálculos.
4) Útil para depurar descomposiciones.

### Ejercicio 5: Potencia de matriz

**Enunciado (contexto IA):** Si $Av=1.2v$, calcula $A^5v$.

**Solución paso a paso:**

1) Aplicación repetida: $A^kv=1.2^k v$.
2) $A^5v=1.2^5v=2.4883v$.
3) Modo crece si $|\lambda|>1$.
4) IA: explica explosión en RNN.

### Ejercicio 6: Estabilidad dinámica

**Enunciado (contexto IA):** Para $x_{t+1}=Ax_t$ con radio espectral 0.8, comportamiento.

**Solución paso a paso:**

1) Todos modos satisfacen $|\lambda|<1$.
2) Estado tiende a 0 al crecer t.
3) Sistema estable.
4) Relevante en modelos recurrentes.

### Ejercicio 7: PCA varianza explicada

**Enunciado (contexto IA):** Autovalores de covarianza: (6,2,1). % varianza del primer componente.

**Solución paso a paso:**

1) Varianza total: $9$.
2) Componente 1: $6/9=0.6667$.
3) Explica 66.67%.
4) Selección de dimensionalidad en IA.

### Ejercicio 8: Diagonalización conceptual

**Enunciado (contexto IA):** Condición para diagonalizar en $\mathbb R^n$.

**Solución paso a paso:**

1) Requiere n autovectores LI.
2) Entonces $A=PDP^{-1}$.
3) Cálculo de potencias se simplifica.
4) Utilidad en análisis teórico de redes lineales.

### Ejercicio 9: Matriz simétrica

**Enunciado (contexto IA):** ¿Qué propiedad espectral tiene una matriz simétrica real?

**Solución paso a paso:**

1) Autovalores reales.
2) Autovectores ortogonales.
3) Diagonalizable por matriz ortogonal.
4) Clave en PCA (covarianza es simétrica).

### Ejercicio 10: Regularización espectral

**Enunciado (contexto IA):** Si mayor autovalor de Hessiano es 100, ¿por qué reducir LR?

**Solución paso a paso:**

1) Curvatura alta implica pasos grandes inestables.
2) LR pequeño evita sobrepasar mínimo.
3) Relación aproximada: $\eta<2/\lambda_{max}$ en caso cuadrático.
4) IA: tuning de estabilidad de entrenamiento.
