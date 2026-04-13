---
layout: default
---
# Sesion 3: Ejercicios de Matrices

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye procedimiento detallado y cierre conceptual aplicado.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Producto matricial en inferencia

**Enunciado (contexto IA):** Con $W=\begin{pmatrix}1&-1\\2&0\end{pmatrix}$ y $x=\begin{pmatrix}3\\4\end{pmatrix}$, calcula $Wx$.

**Solución paso a paso:**

1) Fila1: $1(3)+(-1)(4)=-1$.
2) Fila2: $2(3)+0(4)=6$.
3) Resultado: $(-1,6)^T$.
4) IA: salida pre-activación de una capa lineal.

### Ejercicio 2: Transpuesta y gradiente

**Enunciado (contexto IA):** Si $X=\begin{pmatrix}1&2\\3&4\\5&6\end{pmatrix}$, halla $X^TX$.

**Solución paso a paso:**

1) $X^T=\begin{pmatrix}1&3&5\\2&4&6\end{pmatrix}$.
2) Multiplica: $X^TX=\begin{pmatrix}35&44\\44&56\end{pmatrix}$.
3) Matriz simétrica positiva semidefinida.
4) Aparece en ecuaciones normales y PCA.

### Ejercicio 3: Determinante e invertibilidad

**Enunciado (contexto IA):** Para $A=\begin{pmatrix}2&4\\1&2\end{pmatrix}$ decide si es invertible.

**Solución paso a paso:**

1) $\det(A)=2(2)-4(1)=0$.
2) Determinante cero implica no invertible.
3) Columnas linealmente dependientes.
4) IA: problemas numéricos en regresión sin regularización.

### Ejercicio 4: Inversa aplicada

**Enunciado (contexto IA):** Resuelve $A\theta=b$ con $A=\begin{pmatrix}2&1\\1&1\end{pmatrix}$, $b=\begin{pmatrix}5\\3\end{pmatrix}$.

**Solución paso a paso:**

1) $A^{-1}=\begin{pmatrix}1&-1\\-1&2\end{pmatrix}$ (det=1).
2) $\theta=A^{-1}b=\begin{pmatrix}2\\1\end{pmatrix}$.
3) Verifica: $A\theta=b$.
4) Interpretable como solución exacta lineal.

### Ejercicio 5: Rango y features redundantes

**Enunciado (contexto IA):** Para $X=\begin{pmatrix}1&2\\2&4\\3&6\end{pmatrix}$ calcula rango e implicación.

**Solución paso a paso:**

1) Columna2=2*columna1.
2) Rango=1.
3) Hay redundancia total de features.
4) IA: multicolinealidad, conviene regularizar o reducir dimensión.

### Ejercicio 6: Covarianza simplificada

**Enunciado (contexto IA):** Datos centrados $X=\begin{pmatrix}1&0\\0&1\\-1&-1\end{pmatrix}$, calcula $\Sigma=\frac{1}{n-1}X^TX$.

**Solución paso a paso:**

1) $X^TX=\begin{pmatrix}2&1\\1&2\end{pmatrix}$.
2) $n=3$, divide por 2.
3) $\Sigma=\begin{pmatrix}1&0.5\\0.5&1\end{pmatrix}$.
4) Base para PCA y análisis de correlación.

### Ejercicio 7: Costo de multiplicación

**Enunciado (contexto IA):** Dimensiones: $A(128\times256)$ y $B(256\times64)$. Dimensión y costo aproximado.

**Solución paso a paso:**

1) Resultado: $(128\times64)$.
2) Multiplicaciones: $128\cdot256\cdot64\approx2.1$ millones.
3) IA: relevante para estimar latencia de capas densas.
4) Optimización de hardware depende de esto.

### Ejercicio 8: Norma Frobenius de pesos

**Enunciado (contexto IA):** $W=\begin{pmatrix}1&-2\\2&1\end{pmatrix}$, calcula $||W||_F^2$.

**Solución paso a paso:**

1) Cuadrados: $1,4,4,1$.
2) Suma: $10$.
3) $||W||_F=\sqrt{10}$.
4) L2 weight decay usa este tipo de magnitud.

### Ejercicio 9: Traza en lineal algebra ML

**Enunciado (contexto IA):** Calcula traza de $A=\begin{pmatrix}4&1&0\\0&3&2\\1&0&5\end{pmatrix}$ y relación con autovalores.

**Solución paso a paso:**

1) Traza: $4+3+5=12$.
2) Igual a suma de autovalores.
3) Ayuda a validar descomposiciones.
4) Útil en análisis espectral de modelos.

### Ejercicio 10: Atención simplificada

**Enunciado (contexto IA):** Con $Q=\begin{pmatrix}1&0\end{pmatrix}$ y $K=\begin{pmatrix}1&0\\0&1\end{pmatrix}$, calcula $QK^T$.

**Solución paso a paso:**

1) $K^T=\begin{pmatrix}1&0\\0&1\end{pmatrix}$.
2) Producto: $QK^T=(1,0)$.
3) Primer token recibe score mayor.
4) Luego softmax convierte scores en pesos de atención.
