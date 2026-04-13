---
layout: default
---
# Sesión 3: Matrices

### Teoría

#### 1. Definición de matriz

Una matriz es un arreglo rectangular de números (reales o complejos) dispuestos en filas y columnas. Se denota con letras mayúsculas: $A, B, W, X$, etc.

$$
A = \begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{pmatrix}
$$

- $m$: número de filas
- $n$: número de columnas
- Se dice que la matriz es de tamaño $m \times n$ (se lee "m por n").
- El elemento $a_{ij}$ está en la fila $i$ y columna $j$.

**Ejemplo:**
$$
A = \begin{pmatrix}
2 & -1 & 0 \\
5 & 3 & -2
\end{pmatrix}
$$
es una matriz de $2 \times 3$. Aquí $a_{11}=2$, $a_{12}=-1$, $a_{13}=0$, $a_{21}=5$, $a_{22}=3$, $a_{23}=-2$.

#### 2. Tipos de matrices

- **Matriz cuadrada:** $m = n$. Ejemplo: $ \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} $
- **Matriz diagonal:** Matriz cuadrada con ceros fuera de la diagonal principal. Ejemplo: $ \begin{pmatrix} 5 & 0 & 0 \\ 0 & -2 & 0 \\ 0 & 0 & 3 \end{pmatrix} $
- **Matriz identidad:** Matriz diagonal con unos en la diagonal. Se denota $I_n$. Ejemplo: $I_3 = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}$
- **Matriz triangular superior:** Todos los elementos debajo de la diagonal son cero. Ejemplo: $ \begin{pmatrix} 2 & 1 & 4 \\ 0 & 3 & -1 \\ 0 & 0 & 5 \end{pmatrix} $
- **Matriz triangular inferior:** Todos los elementos arriba de la diagonal son cero. Ejemplo: $ \begin{pmatrix} 2 & 0 & 0 \\ 3 & 1 & 0 \\ -2 & 4 & 5 \end{pmatrix} $

#### 3. Vectores como matrices de una columna

Un vector columna de dimensión $n$ puede verse como una matriz de $n \times 1$:
$$
\mathbf{v} = \begin{pmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{pmatrix}
$$
Un vector fila es una matriz de $1 \times n$:
$$
\mathbf{v}^T = \begin{pmatrix} v_1 & v_2 & \cdots & v_n \end{pmatrix}
$$

**Operaciones con vectores (como matrices):**
- **Suma:** $\mathbf{u} + \mathbf{v}$ se realiza elemento a elemento (misma dimensión).
- **Resta:** $\mathbf{u} - \mathbf{v}$.
- **Multiplicación por escalar:** $\alpha \mathbf{v}$ multiplica cada componente.

**Ejemplo paso a paso:**
Sean $\mathbf{u} = \begin{pmatrix} 2 \\ -1 \\ 3 \end{pmatrix}$, $\mathbf{v} = \begin{pmatrix} 0 \\ 5 \\ -2 \end{pmatrix}$, y escalar $\alpha = 3$.
- $\mathbf{u} + \mathbf{v} = \begin{pmatrix} 2+0 \\ -1+5 \\ 3+(-2) \end{pmatrix} = \begin{pmatrix} 2 \\ 4 \\ 1 \end{pmatrix}$
- $\mathbf{u} - \mathbf{v} = \begin{pmatrix} 2-0 \\ -1-5 \\ 3-(-2) \end{pmatrix} = \begin{pmatrix} 2 \\ -6 \\ 5 \end{pmatrix}$
- $\alpha \mathbf{u} = \begin{pmatrix} 3\cdot 2 \\ 3\cdot (-1) \\ 3\cdot 3 \end{pmatrix} = \begin{pmatrix} 6 \\ -3 \\ 9 \end{pmatrix}$

#### 4. Operaciones con matrices

##### Suma de matrices
Dos matrices del mismo tamaño se suman elemento a elemento:
$$
(A + B)_{ij} = a_{ij} + b_{ij}
$$

**Ejemplo:**
$$
A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}, \quad
B = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix}
$$
$$
A + B = \begin{pmatrix} 1+5 & 2+6 \\ 3+7 & 4+8 \end{pmatrix} = \begin{pmatrix} 6 & 8 \\ 10 & 12 \end{pmatrix}
$$

##### Producto de matrices
El producto $C = AB$ solo está definido si el número de columnas de $A$ es igual al número de filas de $B$. Si $A$ es $m \times n$ y $B$ es $n \times p$, entonces $C$ es $m \times p$. El elemento $(i,j)$ de $C$ se calcula como:
$$
c_{ij} = \sum_{k=1}^{n} a_{ik} b_{kj}
$$
Es decir, el producto punto de la fila $i$ de $A$ con la columna $j$ de $B$.

**Ejemplo paso a paso:**
$$
A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}, \quad
B = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix}
$$
Calculemos $C = AB$:

- $c_{11} = a_{11}b_{11} + a_{12}b_{21} = 1\cdot5 + 2\cdot7 = 5 + 14 = 19$
- $c_{12} = a_{11}b_{12} + a_{12}b_{22} = 1\cdot6 + 2\cdot8 = 6 + 16 = 22$
- $c_{21} = a_{21}b_{11} + a_{22}b_{21} = 3\cdot5 + 4\cdot7 = 15 + 28 = 43$
- $c_{22} = a_{21}b_{12} + a_{22}b_{22} = 3\cdot6 + 4\cdot8 = 18 + 32 = 50$

$$
C = \begin{pmatrix} 19 & 22 \\ 43 & 50 \end{pmatrix}
$$

**Propiedades importantes (no conmutativo):** En general $AB \neq BA$.

##### Multiplicación matriz–vector
Es un caso particular del producto de matrices: si $A$ es $m \times n$ y $\mathbf{x}$ es un vector columna $n \times 1$, entonces $A\mathbf{x}$ es un vector $m \times 1$:
$$
(A\mathbf{x})_i = \sum_{k=1}^{n} a_{ik} x_k
$$

**Ejemplo:**
$$
A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}, \quad
\mathbf{x} = \begin{pmatrix} 5 \\ 6 \end{pmatrix}
$$
$$
A\mathbf{x} = \begin{pmatrix} 1\cdot5 + 2\cdot6 \\ 3\cdot5 + 4\cdot6 \end{pmatrix} = \begin{pmatrix} 5+12 \\ 15+24 \end{pmatrix} = \begin{pmatrix} 17 \\ 39 \end{pmatrix}
$$

##### Transposición
La transpuesta de una matriz $A$ de tamaño $m \times n$ es una matriz $A^T$ de tamaño $n \times m$ donde las filas se convierten en columnas: $(A^T)_{ij} = a_{ji}$.

**Ejemplo:**
$$
A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{pmatrix} \Rightarrow
A^T = \begin{pmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{pmatrix}
$$

#### 5. Propiedades de matrices

##### Determinante (para matrices cuadradas)
El determinante es un número asociado a una matriz cuadrada que indica, entre otras cosas, si la matriz es invertible (determinante ≠ 0). Para una matriz $2 \times 2$:
$$
\det\begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad - bc
$$

**Ejemplo:**
$$
A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} \Rightarrow \det(A) = 1\cdot4 - 2\cdot3 = 4 - 6 = -2
$$

##### Matriz inversa
La inversa de una matriz cuadrada $A$ (si existe) es otra matriz $A^{-1}$ tal que $A A^{-1} = A^{-1} A = I$. Para una matriz $2 \times 2$:
$$
A^{-1} = \frac{1}{\det(A)} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}
$$
si $\det(A) \neq 0$.

**Ejemplo:** Con $A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}$, $\det(A) = -2$, entonces:
$$
A^{-1} = \frac{1}{-2} \begin{pmatrix} 4 & -2 \\ -3 & 1 \end{pmatrix} = \begin{pmatrix} -2 & 1 \\ 1.5 & -0.5 \end{pmatrix}
$$
Verificación: $A A^{-1} = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} \begin{pmatrix} -2 & 1 \\ 1.5 & -0.5 \end{pmatrix} = \begin{pmatrix} -2+3 & 1-1 \\ -6+6 & 3-2 \end{pmatrix} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$

##### Rango de una matriz
El rango es el número máximo de filas (o columnas) linealmente independientes. Indica la dimensión del espacio generado por las filas o columnas. En IA, el rango está relacionado con la cantidad de información útil en una matriz de datos.

**Ejemplo:** La matriz $\begin{pmatrix} 1 & 2 \\ 2 & 4 \end{pmatrix}$ tiene rango 1 porque la segunda fila es múltiplo de la primera.

#### 6. Representación de datasets como matrices

En Machine Learning, un conjunto de datos con $n$ muestras y $d$ características se representa típicamente como una matriz $X$ de tamaño $n \times d$:

$$
X = \begin{pmatrix}
x_{11} & x_{12} & \cdots & x_{1d} \\
x_{21} & x_{22} & \cdots & x_{2d} \\
\vdots & \vdots & \ddots & \vdots \\
x_{n1} & x_{n2} & \cdots & x_{nd}
\end{pmatrix}
$$
donde cada fila $i$ corresponde a la $i$-ésima muestra, y cada columna $j$ corresponde a la $j$-ésima característica (feature).

**Ejemplo:** Un dataset de 3 casas con características: área (m²), número de habitaciones, antigüedad (años).
$$
X = \begin{pmatrix}
120 & 3 & 10 \\
85 & 2 & 5 \\
200 & 4 & 2
\end{pmatrix}
$$
La primera fila representa una casa de 120 m², 3 habitaciones y 10 años.

Además, el vector de etiquetas (valores a predecir) se representa como un vector columna:
$$
\mathbf{y} = \begin{pmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{pmatrix}
$$
Por ejemplo, precios de las casas: $\mathbf{y} = \begin{pmatrix} 250000 \\ 180000 \\ 320000 \end{pmatrix}$.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Regresión lineal (representación matricial)
En regresión lineal múltiple, el modelo es:
$$
\hat{\mathbf{y}} = X \mathbf{w} + b
$$
donde:
- $X$ es la matriz de diseño $n \times d$ (cada fila es una muestra),
- $\mathbf{w}$ es el vector de pesos $d \times 1$,
- $b$ es el sesgo (escalar).

Para incluir el sesgo, se puede aumentar $X$ con una columna de unos:
$$
X_{\text{aug}} = \begin{pmatrix} 1 & x_{11} & x_{12} & \cdots & x_{1d} \\ 1 & x_{21} & x_{22} & \cdots & x_{2d} \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ 1 & x_{n1} & x_{n2} & \cdots & x_{nd} \end{pmatrix}, \quad
\boldsymbol{\theta} = \begin{pmatrix} b \\ w_1 \\ w_2 \\ \vdots \\ w_d \end{pmatrix}
$$
Entonces $\hat{\mathbf{y}} = X_{\text{aug}} \boldsymbol{\theta}$.

**Solución analítica (mínimos cuadrados):**
$$
\boldsymbol{\theta} = (X_{\text{aug}}^T X_{\text{aug}})^{-1} X_{\text{aug}}^T \mathbf{y}
$$
Esta fórmula utiliza **producto de matrices**, **transposición** e **inversa**. Es un ejemplo clásico de cómo las operaciones matriciales resuelven un problema de optimización.

**Ejemplo numérico pequeño:**  
Supongamos 2 muestras con una característica:  
$X = \begin{pmatrix} 1 \\ 2 \end{pmatrix}$, $\mathbf{y} = \begin{pmatrix} 2 \\ 3 \end{pmatrix}$.  
Aumentamos: $X_{\text{aug}} = \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix}$.  
Calculamos:
- $X_{\text{aug}}^T X_{\text{aug}} = \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix}^T \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix} = \begin{pmatrix} 2 & 3 \\ 3 & 5 \end{pmatrix}$
- Inversa: $\det = 2\cdot5 - 3\cdot3 = 10-9=1$, entonces inversa = $\begin{pmatrix} 5 & -3 \\ -3 & 2 \end{pmatrix}$
- $X_{\text{aug}}^T \mathbf{y} = \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix}^T \begin{pmatrix} 2 \\ 3 \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ 1 & 2 \end{pmatrix} \begin{pmatrix} 2 \\ 3 \end{pmatrix} = \begin{pmatrix} 5 \\ 8 \end{pmatrix}$
- $\boldsymbol{\theta} = \begin{pmatrix} 5 & -3 \\ -3 & 2 \end{pmatrix} \begin{pmatrix} 5 \\ 8 \end{pmatrix} = \begin{pmatrix} 25 - 24 \\ -15 + 16 \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$
Así, $b=1$, $w=1$, modelo: $\hat{y} = 1 + 1\cdot x$.

##### 2. Regresión logística (matriz de features)
En regresión logística, la combinación lineal se escribe como:
$$
\mathbf{z} = X \mathbf{w} + b
$$
y luego se aplica la sigmoide: $\hat{\mathbf{y}} = \sigma(\mathbf{z})$. La matriz $X$ juega el mismo papel que en regresión lineal.

##### 3. PCA (matriz de covarianza)
En Análisis de Componentes Principales, partimos de la matriz de datos $X$ (centrada, es decir, con media cero por columnas). La matriz de covarianza se calcula como:
$$
\Sigma = \frac{1}{n-1} X^T X
$$
(notar que $X^T X$ es un producto matricial). Luego, los autovalores y autovectores de $\Sigma$ dan las direcciones principales.

##### 4. Factorización matricial en sistemas de recomendación
En sistemas de recomendación como el de Netflix, se tiene una matriz $R$ de usuarios × ítems con calificaciones (muchas celdas vacías). La factorización matricial busca aproximar $R \approx P Q^T$, donde $P$ y $Q$ son matrices de factores latentes. Esto implica operaciones matriciales y descomposiciones.

#### Deep Learning (DL)

##### 1. Pesos como matrices en capas lineales
En una red neuronal, cada capa lineal (fully connected) realiza la operación:
$$
\mathbf{h} = W \mathbf{x} + \mathbf{b}
$$
donde:
- $\mathbf{x}$ es el vector de entrada (tamaño $d_{\text{in}}$),
- $W$ es la matriz de pesos de tamaño $d_{\text{out}} \times d_{\text{in}}$,
- $\mathbf{b}$ es el vector de sesgo de tamaño $d_{\text{out}}$,
- $\mathbf{h}$ es la salida (pre-activación).

Esta es una **multiplicación matriz–vector** más suma.

**Ejemplo:** Una capa que recibe una entrada de 3 características y produce 2 neuronas:
$$
W = \begin{pmatrix} 0.2 & -0.5 & 0.1 \\ 0.8 & 0.3 & -0.2 \end{pmatrix}, \quad
\mathbf{b} = \begin{pmatrix} 0.1 \\ -0.1 \end{pmatrix}, \quad
\mathbf{x} = \begin{pmatrix} 1.0 \\ 0.5 \\ -1.0 \end{pmatrix}
$$
$$
W\mathbf{x} = \begin{pmatrix} 0.2\cdot1 + (-0.5)\cdot0.5 + 0.1\cdot(-1) \\ 0.8\cdot1 + 0.3\cdot0.5 + (-0.2)\cdot(-1) \end{pmatrix}
= \begin{pmatrix} 0.2 -0.25 -0.1 \\ 0.8 +0.15 +0.2 \end{pmatrix}
= \begin{pmatrix} -0.15 \\ 1.15 \end{pmatrix}
$$
$$
\mathbf{h} = W\mathbf{x} + \mathbf{b} = \begin{pmatrix} -0.15+0.1 \\ 1.15-0.1 \end{pmatrix} = \begin{pmatrix} -0.05 \\ 1.05 \end{pmatrix}
$$

##### 2. Backpropagation (operaciones matriciales)
Durante el entrenamiento, el gradiente de la pérdida respecto a los pesos se calcula usando la regla de la cadena. Para una capa lineal, si conocemos el gradiente de la pérdida respecto a la salida $\frac{\partial L}{\partial \mathbf{h}}$, entonces:
$$
\frac{\partial L}{\partial W} = \frac{\partial L}{\partial \mathbf{h}} \cdot \mathbf{x}^T
$$
que es un **producto exterior** (resultado de multiplicar un vector columna por un vector fila, generando una matriz). Además, el gradiente respecto a la entrada es:
$$
\frac{\partial L}{\partial \mathbf{x}} = W^T \frac{\partial L}{\partial \mathbf{h}}
$$
que es otra **multiplicación matriz–vector**. Así, las operaciones matriciales son el corazón del backpropagation.

##### 3. Inicialización de pesos
La inicialización adecuada de las matrices de pesos es crucial para evitar gradientes evanescentes/explosivos. Por ejemplo, la inicialización de Xavier (Glorot) propone que los pesos se muestreen de una distribución con varianza:
$$
\text{Var}(W) = \frac{2}{n_{\text{in}} + n_{\text{out}}}
$$
Esto depende del tamaño de las matrices (número de filas y columnas).

##### 4. Convoluciones (operaciones matriciales)
Aunque las convoluciones se implementan eficientemente con técnicas como im2col (convertir parches en columnas), en el fondo son operaciones matriciales. Por ejemplo, una convolución 2D puede verse como una multiplicación de una matriz que contiene los parches de la imagen con la matriz de kernels.

##### 5. Transformers (multiplicación de matrices en atención)
En el mecanismo de atención, se calculan las matrices de consultas (Q), claves (K) y valores (V) mediante multiplicaciones de la entrada con matrices de pesos:
$$
Q = X W_Q, \quad K = X W_K, \quad V = X W_V
$$
Luego, los pesos de atención se obtienen con:
$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{Q K^T}{\sqrt{d_k}}\right) V
$$
Aquí, $Q K^T$ es un **producto de matrices** (de tamaño secuencia × secuencia), y luego se multiplica por $V$. Todo el mecanismo depende críticamente de operaciones matriciales eficientes.

---

**Conclusión de la semana:** Las matrices son el lenguaje natural para representar datos y operaciones en IA. Desde la representación de datasets hasta las operaciones en redes neuronales, el álgebra matricial es omnipresente. Dominar estas operaciones y propiedades es esencial para entender cómo funcionan internamente los modelos y para poder implementarlos eficientemente.