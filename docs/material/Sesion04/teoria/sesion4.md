---
layout: default
---
# Sesión 4: Sistemas de Ecuaciones Lineales

### Teoría

#### 1. Sistemas lineales: representación $Ax = b$

Un sistema de ecuaciones lineales es un conjunto de ecuaciones de la forma:

$$
\begin{cases}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n = b_1 \\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n = b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n = b_m
\end{cases}
$$

Este sistema puede escribirse en forma matricial como:

$$
A \mathbf{x} = \mathbf{b}
$$

donde:
- $A$ es la matriz de coeficientes de tamaño $m \times n$,
- $\mathbf{x}$ es el vector columna de incógnitas de tamaño $n \times 1$,
- $\mathbf{b}$ es el vector columna de términos independientes de tamaño $m \times 1$.

**Ejemplo 1 (2 ecuaciones, 2 incógnitas):**

$$
\begin{cases}
2x + 3y = 8 \\
x - y = -1
\end{cases}
\quad\Rightarrow\quad
\begin{pmatrix} 2 & 3 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 8 \\ -1 \end{pmatrix}
$$

**Ejemplo 2 (3 ecuaciones, 3 incógnitas):**

$$
\begin{cases}
x + y + z = 6 \\
2y + z = 4 \\
x - y = 1
\end{cases}
\quad\Rightarrow\quad
\begin{pmatrix} 1 & 1 & 1 \\ 0 & 2 & 1 \\ 1 & -1 & 0 \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 6 \\ 4 \\ 1 \end{pmatrix}
$$

#### 2. Interpretación geométrica

Cada ecuación lineal representa un **hiperplano** en $\mathbb{R}^n$:
- En 2D: una recta.
- En 3D: un plano.
- En $n$-D: un hiperplano.

**Tipos de solución según la intersección de hiperplanos:**

- **Solución única:** Los hiperplanos se intersectan en un solo punto.  
  *Ejemplo en 2D:* dos rectas no paralelas que se cruzan.
- **Infinitas soluciones:** Los hiperplanos coinciden o se intersectan en una recta (o plano, etc.).  
  *Ejemplo:* dos rectas coincidentes o dos planos que se cortan en una recta.
- **Sin solución (inconsistente):** Los hiperplanos son paralelos o no se intersectan.  
  *Ejemplo:* dos rectas paralelas distintas.

**Ejemplo gráfico en 2D:**

- Solución única:  
  $y = 2x + 1$ y $y = -x + 4$ se cruzan en $(1,3)$.
- Infinitas soluciones:  
  $y = 2x + 1$ y $2y = 4x + 2$ son la misma recta.
- Inconsistente:  
  $y = 2x + 1$ y $y = 2x - 3$ son paralelas y no se tocan.

#### 3. Eliminación gaussiana

Método sistemático para resolver sistemas lineales transformando la matriz aumentada $[A|\mathbf{b}]$ en una forma escalonada (triangular superior) mediante operaciones elementales:

1. Intercambiar filas.
2. Multiplicar una fila por un escalar no nulo.
3. Sumar un múltiplo de una fila a otra.

**Ejemplo paso a paso:** Resolver el sistema

$$
\begin{cases}
x + y + z = 6 \\
2y + z = 4 \\
x - y = 1
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
0 & 2 & 1 & 4 \\
1 & -1 & 0 & 1
\end{array}\right]
$$

**Paso 1:** Eliminar $x$ de la tercera fila: $F_3 \leftarrow F_3 - F_1$

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
0 & 2 & 1 & 4 \\
0 & -2 & -1 & -5
\end{array}\right]
$$

**Paso 2:** Eliminar $y$ de la tercera fila: $F_3 \leftarrow F_3 + F_2$

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
0 & 2 & 1 & 4 \\
0 & 0 & 0 & -1
\end{array}\right]
$$

La última fila dice $0 = -1$, lo que es imposible. El sistema es **inconsistente** (no tiene solución).

**Ejemplo con solución única:** Resolver

$$
\begin{cases}
2x + 3y = 8 \\
x - y = -1
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{cc|c}
2 & 3 & 8 \\
1 & -1 & -1
\end{array}\right]
$$

Intercambiamos filas para tener pivote 1:

$$
\left[\begin{array}{cc|c}
1 & -1 & -1 \\
2 & 3 & 8
\end{array}\right]
$$

Eliminamos $x$ de la segunda fila: $F_2 \leftarrow F_2 - 2F_1$

$$
\left[\begin{array}{cc|c}
1 & -1 & -1 \\
0 & 5 & 10
\end{array}\right]
$$

Sustitución hacia atrás:
- De la segunda fila: $5y = 10 \Rightarrow y = 2$.
- De la primera: $x - 2 = -1 \Rightarrow x = 1$.

Solución: $x = 1,\; y = 2$.

#### 4. Tipos de solución

- **Solución única:** La matriz $A$ es cuadrada e invertible (rango completo, $\det(A) \neq 0$).
- **Infinitas soluciones:** Hay variables libres. Por ejemplo:

  $$
  \begin{cases}
  x + y = 3 \\
  2x + 2y = 6
  \end{cases}
  $$
  La segunda ecuación es múltiplo de la primera. Soluciones: $x = t,\; y = 3 - t$ para cualquier $t$.

- **Sistema inconsistente:** No hay solución. Ejemplo:

  $$
  \begin{cases}
  x + y = 3 \\
  x + y = 5
  \end{cases}
  $$

#### 5. Sistemas sobredeterminados y solución por mínimos cuadrados

Un sistema es **sobredeterminado** cuando hay más ecuaciones que incógnitas ($m > n$). Generalmente no tiene solución exacta, pero podemos buscar una solución aproximada que minimice el error.

Dado $A\mathbf{x} \approx \mathbf{b}$, queremos minimizar $\|A\mathbf{x} - \mathbf{b}\|^2$. La solución de **mínimos cuadrados** satisface las **ecuaciones normales**:

$$
A^T A \mathbf{x} = A^T \mathbf{b}
$$

Si $A^T A$ es invertible, la solución es:

$$
\mathbf{x} = (A^T A)^{-1} A^T \mathbf{b}
$$

**Interpretación geométrica:** La solución de mínimos cuadrados es la proyección ortogonal de $\mathbf{b}$ sobre el espacio columna de $A$.

**Ejemplo numérico:** Ajustar una recta $y = mx$ (sin intercepto) a los puntos $(1,2), (2,3), (3,5)$.

El sistema sería:

$$
\begin{cases}
m \cdot 1 = 2 \\
m \cdot 2 = 3 \\
m \cdot 3 = 5
\end{cases}
\quad\Rightarrow\quad
A = \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix},\quad
\mathbf{b} = \begin{pmatrix} 2 \\ 3 \\ 5 \end{pmatrix}
$$

Ecuaciones normales:

$$
A^T A = (1\;2\;3) \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix} = 1^2 + 2^2 + 3^2 = 14
$$
$$
A^T \mathbf{b} = (1\;2\;3) \begin{pmatrix} 2 \\ 3 \\ 5 \end{pmatrix} = 1\cdot2 + 2\cdot3 + 3\cdot5 = 2 + 6 + 15 = 23
$$

Solución:

$$
m = \frac{23}{14} \approx 1.6429
$$

La recta es $y = 1.6429x$. El error cuadrático total es mínimo.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Regresión lineal (mínimos cuadrados)

La regresión lineal es el ejemplo por excelencia de un problema de mínimos cuadrados. Dado un conjunto de datos $(x_i, y_i)$ con $i = 1,\dots,n$, se busca la recta (o hiperplano) que mejor se ajusta.

Para el caso de una variable con intercepto, el modelo es:

$$
\hat{y}_i = w x_i + b
$$

Queremos minimizar la suma de errores cuadrados:

$$
L(w,b) = \sum_{i=1}^n (y_i - (w x_i + b))^2
$$

En forma matricial, definimos:

$$
X = \begin{pmatrix}
1 & x_1 \\
1 & x_2 \\
\vdots & \vdots \\
1 & x_n
\end{pmatrix},\quad
\mathbf{y} = \begin{pmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{pmatrix},\quad
\boldsymbol{\theta} = \begin{pmatrix} b \\ w \end{pmatrix}
$$

Entonces:

$$
L(\boldsymbol{\theta}) = \| X\boldsymbol{\theta} - \mathbf{y} \|^2
$$

La solución de mínimos cuadrados es:

$$
\boldsymbol{\theta} = (X^T X)^{-1} X^T \mathbf{y}
$$

**Ejemplo paso a paso con los mismos puntos $(1,2), (2,3), (3,5)$ pero con intercepto:**

Construimos $X$ y $\mathbf{y}$:

$$
X = \begin{pmatrix}
1 & 1 \\
1 & 2 \\
1 & 3
\end{pmatrix},\quad
\mathbf{y} = \begin{pmatrix} 2 \\ 3 \\ 5 \end{pmatrix}
$$

Calculamos:

$$
X^T X = \begin{pmatrix}
1 & 1 & 1 \\
1 & 2 & 3
\end{pmatrix}
\begin{pmatrix}
1 & 1 \\
1 & 2 \\
1 & 3
\end{pmatrix}
= \begin{pmatrix}
3 & 6 \\
6 & 14
\end{pmatrix}
$$

$$
X^T \mathbf{y} = \begin{pmatrix}
1 & 1 & 1 \\
1 & 2 & 3
\end{pmatrix}
\begin{pmatrix} 2 \\ 3 \\ 5 \end{pmatrix}
= \begin{pmatrix}
2+3+5 \\
2+6+15
\end{pmatrix}
= \begin{pmatrix} 10 \\ 23 \end{pmatrix}
$$

Inversa de $X^T X$:

$$
\det\begin{pmatrix} 3 & 6 \\ 6 & 14 \end{pmatrix} = 3\cdot14 - 6\cdot6 = 42 - 36 = 6
$$
$$
(X^T X)^{-1} = \frac{1}{6} \begin{pmatrix} 14 & -6 \\ -6 & 3 \end{pmatrix}
$$

Finalmente:

$$
\boldsymbol{\theta} = \frac{1}{6} \begin{pmatrix} 14 & -6 \\ -6 & 3 \end{pmatrix} \begin{pmatrix} 10 \\ 23 \end{pmatrix}
= \frac{1}{6} \begin{pmatrix} 140 - 138 \\ -60 + 69 \end{pmatrix}
= \frac{1}{6} \begin{pmatrix} 2 \\ 9 \end{pmatrix}
= \begin{pmatrix} 0.3333 \\ 1.5 \end{pmatrix}
$$

Así, $b = 0.3333$, $w = 1.5$. La recta es:

$$
y = 1.5x + 0.3333
$$

Comprobación:
- Para $x = 1$: $y = 1.833$ (cerca de 2)
- Para $x = 2$: $y = 3.333$ (cerca de 3)
- Para $x = 3$: $y = 4.833$ (cerca de 5)

El error cuadrático es menor que con la recta sin intercepto.

##### 2. Otros modelos lineales

- **Ridge regression:** Añade regularización L2, modificando las ecuaciones normales a:

  $$
  (X^T X + \lambda I) \boldsymbol{\theta} = X^T \mathbf{y}
  $$

  Esto sigue siendo un sistema lineal (aunque ahora la matriz es definida positiva y siempre invertible).

- **Lasso:** No tiene solución cerrada, pero se basa en optimización con normas L1. Sin embargo, en cada iteración de algoritmos como el descenso de coordenadas se resuelven problemas univariantes que son esencialmente ecuaciones lineales.

- **PCA:** La descomposición en componentes principales requiere resolver un problema de autovalores para la matriz de covarianza $X^T X$, que está relacionado con sistemas lineales homogéneos $(X^T X - \lambda I)\mathbf{v} = 0$.

#### Deep Learning (DL)

##### Base conceptual para optimización

Aunque en deep learning no se resuelven sistemas lineales directamente (excepto en capas lineales sin activación), el concepto subyace en varios aspectos:

- **Inicialización y análisis:** Una red neuronal sin funciones de activación (totalmente lineal) sería simplemente una composición de transformaciones lineales, equivalente a una única transformación lineal. Esto lleva a considerar el rango y la dimensión del espacio de representaciones, que son conceptos ligados a sistemas lineales.

- **Backpropagation:** En cada capa, el cálculo del gradiente involucra multiplicaciones matriciales que pueden verse como la solución de sistemas lineales locales (aunque no se resuelven mediante eliminación gaussiana sino directamente). Por ejemplo, para una capa lineal con salida $\mathbf{h} = W\mathbf{x} + \mathbf{b}$, si conocemos $\frac{\partial L}{\partial \mathbf{h}}$, entonces:

  $$
  \frac{\partial L}{\partial W} = \frac{\partial L}{\partial \mathbf{h}} \mathbf{x}^T
  $$
  que es un producto exterior, y

  $$
  \frac{\partial L}{\partial \mathbf{x}} = W^T \frac{\partial L}{\partial \mathbf{h}}
  $$
  que es una multiplicación matriz–vector.

- **Optimización de segundo orden:** Algunos optimizadores (como el método de Newton) requieren resolver sistemas lineales con la matriz Hessiana:

  $$
  H \Delta \boldsymbol{\theta} = -\nabla L
  $$

  En la práctica se usan aproximaciones (por ejemplo, L-BFGS) para evitar calcular e invertir la Hessiana, pero la idea fundamental es resolver un sistema lineal.

- **Análisis de estabilidad:** En redes recurrentes, el estudio de gradientes evanescentes o explosivos se relaciona con los autovalores de la matriz de pesos. Los autovalores son las raíces de la ecuación característica $\det(W - \lambda I) = 0$, que proviene de un sistema lineal homogéneo.

- **Regularización:** Técnicas como weight decay (L2) añaden un término lineal a la actualización de gradientes, que puede interpretarse como modificar el sistema lineal subyacente.

**Ejemplo conceptual:** Consideremos una red neuronal con una sola capa lineal y función de pérdida cuadrática. El problema se reduce a mínimos cuadrados, cuya solución analítica es la de las ecuaciones normales. Aunque en la práctica se use gradiente descendente, la solución exacta existe y es la que acabamos de derivar.

---
