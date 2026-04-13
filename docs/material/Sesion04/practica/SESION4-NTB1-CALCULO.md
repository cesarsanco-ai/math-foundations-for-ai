---
layout: default
---
# Sesión 4: Sistemas de Ecuaciones Lineales - Solucionario NTB1

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Resolver sistema de calibración

**Enunciado (contexto IA):** Resuelve $\begin{cases}2x+y=7\\x-y=2\end{cases}$, donde $x,y$ son pesos de dos features.

**Solución paso a paso:**

1) De $x-y=2\Rightarrow y=x-2$.
2) Sustituye en la primera: $2x+(x-2)=7\Rightarrow3x=9\Rightarrow x=3$.
3) Entonces $y=1$.
4) IA: separación de contribuciones de variables.

### Ejercicio 2: Forma matricial para batch

**Enunciado (contexto IA):** Escribe $\{x_1+2x_2=5,\ 3x_1-x_2=4\}$ como $A\mathbf{x}=\mathbf{b}$.

**Solución paso a paso:**

1) Coeficientes a matriz: $A=\begin{pmatrix}1&2\\3&-1\end{pmatrix}$.
2) Vector incógnitas: $\mathbf{x}=(x_1,x_2)^T$.
3) Términos independientes: $\mathbf{b}=(5,4)^T$.
4) Esta notación permite usar álgebra lineal eficiente.

### Ejercicio 3: Eliminación gaussiana

**Enunciado (contexto IA):** Aplica un paso a $\left[\begin{array}{cc|c}1&2&5\\3&-1&4\end{array}\right]$.

**Solución paso a paso:**

1) Haz $F_2\leftarrow F_2-3F_1$.
2) Queda $\left[\begin{array}{cc|c}1&2&5\\0&-7&-11\end{array}\right]$.
3) Luego $x_2=11/7$.
4) Back-substitution da $x_1=13/7$.

### Ejercicio 4: Sistema inconsistente

**Enunciado (contexto IA):** Analiza $\{x+y=1,\ x+y=3\}$.

**Solución paso a paso:**

1) Restar ecuaciones da $0=2$.
2) Contradicción => sin solución.
3) IA: datos con etiquetas incompatibles generan conflicto de ajuste exacto.
4) Se usa ajuste aproximado (mínimos cuadrados).

### Ejercicio 5: Infinitas soluciones

**Enunciado (contexto IA):** Analiza $\{x+2y=4,\ 2x+4y=8\}$.

**Solución paso a paso:**

1) Segunda ecuación es 2 veces la primera.
2) Una sola restricción independiente.
3) Parametriza: $y=t$, $x=4-2t$.
4) IA: multicolinealidad extrema en features.

### Ejercicio 6: Mínimos cuadrados 1D

**Enunciado (contexto IA):** Con $A=(1,2,3)^T$, $b=(1,2,2)^T$, estima $x$ en $Ax\approx b$.

**Solución paso a paso:**

1) Ecuación normal: $x=(A^TA)^{-1}A^Tb$.
2) $A^TA=1+4+9=14$.
3) $A^Tb=1+4+6=11$.
4) $x=11/14=0.7857$.
5) Ajuste óptimo en error cuadrático.

### Ejercicio 7: Residual

**Enunciado (contexto IA):** Si $b=(1,2,2)^T$ y $\hat b=A\hat x=(0.8,1.6,2.4)^T$, calcula residual y norma cuadrada.

**Solución paso a paso:**

1) $r=b-\hat b=(0.2,0.4,-0.4)$.
2) $||r||_2^2=0.04+0.16+0.16=0.36$.
3) Menor residual implica mejor ajuste.
4) Métrica base de regresión lineal.

### Ejercicio 8: Interpretación geométrica

**Enunciado (contexto IA):** Dos planos no paralelos en 3D, ¿qué intersección típica tienen?

**Solución paso a paso:**

1) En general se intersectan en una recta.
2) Si además hay tercer plano, puede fijar punto único.
3) IA: más ecuaciones restringen espacio de parámetros.
4) Con ruido, se busca región de compromiso.

### Ejercicio 9: Ridge como sistema lineal

**Enunciado (contexto IA):** Escribe la ecuación de Ridge para $X, y, \lambda$.

**Solución paso a paso:**

1) Objetivo: $||X\theta-y||_2^2+\lambda||\theta||_2^2$.
2) Condición de óptimo: $(X^TX+\lambda I)\theta=X^Ty$.
3) Siempre mejor condicionado que OLS.
4) IA: robusto ante colinealidad.

### Ejercicio 10: Costo computacional

**Enunciado (contexto IA):** Compara resolver por inversa directa vs gradiente en gran escala.

**Solución paso a paso:**

1) Inversa exacta en d dimensiones cuesta aprox $O(d^3)$.
2) Gradiente por época cuesta aprox $O(nd)$.
3) Para d grande, métodos iterativos son preferibles.
4) IA moderna privilegia optimización iterativa.
