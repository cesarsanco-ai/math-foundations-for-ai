## Semana 7: Autovalores y Autovectores

### Teoría

#### 1. Definición de autovalor y autovector

Sea \(A\) una matriz cuadrada de \(n \times n\). Un vector no nulo \(\mathbf{v} \in \mathbb{R}^n\) es un **autovector** (o vector propio) de \(A\) si existe un escalar \(\lambda \in \mathbb{R}\) (o \(\mathbb{C}\)) tal que:

\[
A \mathbf{v} = \lambda \mathbf{v}
\]

El escalar \(\lambda\) se llama **autovalor** (o valor propio) asociado a \(\mathbf{v}\).

**Interpretación:** El autovector es una dirección que, al aplicarle la transformación lineal representada por \(A\), solo se estira o encoge (cambia de escala) pero no cambia de dirección. El autovalor indica el factor de escala.

**Ejemplo:** Sea \(A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}\). Verifiquemos si \(\mathbf{v} = \begin{pmatrix} 1 \\ 1 \end{pmatrix}\) es autovector:

\[
A \mathbf{v} = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \begin{pmatrix} 5 \\ 5 \end{pmatrix} = 5 \begin{pmatrix} 1 \\ 1 \end{pmatrix}
\]
Por tanto, \(\lambda = 5\) es autovalor y \(\mathbf{v} = (1,1)\) es autovector.

#### 2. Ecuación característica

Para encontrar todos los autovalores, reescribimos la ecuación \(A\mathbf{v} = \lambda \mathbf{v}\) como:

\[
A\mathbf{v} - \lambda \mathbf{v} = \mathbf{0} \quad \Rightarrow \quad (A - \lambda I) \mathbf{v} = \mathbf{0}
\]

Para que exista \(\mathbf{v} \neq \mathbf{0}\), la matriz \(A - \lambda I\) debe ser singular, es decir, su determinante debe ser cero:

\[
\det(A - \lambda I) = 0
\]

Esta ecuación se llama **ecuación característica**. Es un polinomio de grado \(n\) en \(\lambda\) cuyas raíces son los autovalores.

**Ejemplo:** Para \(A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}\):

\[
A - \lambda I = \begin{pmatrix} 4-\lambda & 1 \\ 2 & 3-\lambda \end{pmatrix}
\]
\[
\det(A - \lambda I) = (4-\lambda)(3-\lambda) - 1\cdot 2 = 12 - 4\lambda - 3\lambda + \lambda^2 - 2 = \lambda^2 - 7\lambda + 10
\]
Igualamos a cero: \(\lambda^2 - 7\lambda + 10 = 0\) ⇒ \((\lambda - 2)(\lambda - 5) = 0\) ⇒ \(\lambda_1 = 2\), \(\lambda_2 = 5\).

Para \(\lambda = 5\) ya encontramos \(\mathbf{v} = (1,1)\). Para \(\lambda = 2\), resolvemos \((A - 2I)\mathbf{v} = 0\):

\[
\begin{pmatrix} 2 & 1 \\ 2 & 1 \end{pmatrix} \begin{pmatrix} v_1 \\ v_2 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}
\]
De la primera fila: \(2v_1 + v_2 = 0\) ⇒ \(v_2 = -2v_1\). Tomando \(v_1 = 1\), obtenemos \(\mathbf{v} = (1, -2)\) (cualquier múltiplo es válido).

#### 3. Interpretación geométrica: direcciones invariantes

Geométricamente, los autovectores señalan las direcciones que la transformación lineal \(A\) deja invariantes (solo escala). En ℝ², si \(A\) tiene dos autovalores reales distintos, entonces las direcciones de los autovectores son ejes a lo largo de los cuales la transformación actúa independientemente.

**Ejemplo visual:** Para \(A = \begin{pmatrix} 2 & 0 \\ 0 & 3 \end{pmatrix}\), los autovectores son \((1,0)\) y \((0,1)\) con autovalores 2 y 3. La transformación escala el eje x por 2 y el eje y por 3.

Si los autovalores son complejos, la transformación incluye rotación (no hay direcciones invariantes reales).

#### 4. Diagonalización de matrices

Una matriz \(A\) de \(n \times n\) es **diagonalizable** si existe una matriz invertible \(P\) (cuyas columnas son autovectores linealmente independientes) y una matriz diagonal \(D\) (con los autovalores en la diagonal) tales que:

\[
A = P D P^{-1}
\]

Equivalentemente, \(D = P^{-1} A P\).

**Condición:** \(A\) es diagonalizable si tiene \(n\) autovectores linealmente independientes (lo que ocurre, por ejemplo, si todos los autovalores son distintos, o si es simétrica).

**Ejemplo:** Para \(A = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix}\), autovalores 5 y 2, autovectores \(\mathbf{v}_1 = (1,1)\) y \(\mathbf{v}_2 = (1,-2)\). Construimos:

\[
P = \begin{pmatrix} 1 & 1 \\ 1 & -2 \end{pmatrix}, \quad D = \begin{pmatrix} 5 & 0 \\ 0 & 2 \end{pmatrix}
\]
Verificamos \(P^{-1} A P = D\). Primero calculamos \(P^{-1}\):
\[
\det(P) = 1\cdot(-2) - 1\cdot1 = -2 -1 = -3, \quad P^{-1} = \frac{1}{-3} \begin{pmatrix} -2 & -1 \\ -1 & 1 \end{pmatrix} = \begin{pmatrix} 2/3 & 1/3 \\ 1/3 & -1/3 \end{pmatrix}
\]
Entonces:
\[
P^{-1} A P = \begin{pmatrix} 2/3 & 1/3 \\ 1/3 & -1/3 \end{pmatrix} \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 1 & -2 \end{pmatrix}
\]
Primero \(A P = \begin{pmatrix} 4 & 1 \\ 2 & 3 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 1 & -2 \end{pmatrix} = \begin{pmatrix} 4\cdot1+1\cdot1 & 4\cdot1+1\cdot(-2) \\ 2\cdot1+3\cdot1 & 2\cdot1+3\cdot(-2) \end{pmatrix} = \begin{pmatrix} 5 & 2 \\ 5 & -4 \end{pmatrix}\)
Luego \(P^{-1} (A P) = \begin{pmatrix} 2/3 & 1/3 \\ 1/3 & -1/3 \end{pmatrix} \begin{pmatrix} 5 & 2 \\ 5 & -4 \end{pmatrix} = \begin{pmatrix} (2/3)5 + (1/3)5 & (2/3)2 + (1/3)(-4) \\ (1/3)5 + (-1/3)5 & (1/3)2 + (-1/3)(-4) \end{pmatrix} = \begin{pmatrix} (10/3+5/3)=15/3=5 & (4/3 -4/3)=0 \\ (5/3-5/3)=0 & (2/3+4/3)=6/3=2 \end{pmatrix} = D\).

La diagonalización facilita calcular potencias de \(A\): \(A^k = P D^k P^{-1}\), donde \(D^k\) es simplemente elevar cada autovalor a la \(k\).

#### 5. Descomposición espectral

Para matrices **simétricas** (\(A = A^T\)), los autovalores son reales y los autovectores pueden elegirse ortonormales. Entonces existe una descomposición:

\[
A = Q \Lambda Q^T
\]
donde \(Q\) es una matriz ortogonal (\(Q^T = Q^{-1}\)) cuyas columnas son los autovectores ortonormales, y \(\Lambda\) es diagonal con los autovalores.

Esta es la **descomposición espectral** (también llamada teorema espectral). Además, se puede escribir como suma de proyectores:

\[
A = \sum_{i=1}^{n} \lambda_i \mathbf{q}_i \mathbf{q}_i^T
\]
donde \(\mathbf{q}_i\) son los autovectores ortonormales.

**Ejemplo:** \(A = \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}\). Es simétrica. Autovalores: \(\det\begin{pmatrix} 2-\lambda & 1 \\ 1 & 2-\lambda \end{pmatrix} = (2-\lambda)^2 - 1 = \lambda^2 - 4\lambda + 3 = 0\) ⇒ \(\lambda_1 = 3, \lambda_2 = 1\). Autovectores:
- Para \(\lambda=3\): \((2-3)x + y = 0\) ⇒ \(-x + y = 0\) ⇒ \(y = x\), autovector \((1,1)\) normalizado: \(\mathbf{q}_1 = (1/\sqrt{2}, 1/\sqrt{2})\).
- Para \(\lambda=1\): \((2-1)x + y = 0\) ⇒ \(x + y = 0\) ⇒ \(y = -x\), autovector \((1,-1)\) normalizado: \(\mathbf{q}_2 = (1/\sqrt{2}, -1/\sqrt{2})\).

Entonces:
\[
Q = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}, \quad \Lambda = \begin{pmatrix} 3 & 0 \\ 0 & 1 \end{pmatrix}
\]
Verificamos \(Q \Lambda Q^T\) da \(A\).

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### PCA (Análisis de Componentes Principales)

El PCA es una técnica de reducción de dimensionalidad que busca las direcciones de máxima varianza en los datos. Estas direcciones resultan ser los autovectores de la matriz de covarianza (o de correlación) de los datos.

**Procedimiento:**
1. Dada una matriz de datos \(X\) de \(n\) muestras y \(d\) características, centramos los datos restando la media de cada columna: \(\tilde{X} = X - \mathbf{1}\boldsymbol{\mu}^T\).
2. Calculamos la matriz de covarianza muestral:
   \[
   S = \frac{1}{n-1} \tilde{X}^T \tilde{X}
   \]
   (o la matriz de correlación si las variables están en escalas muy diferentes).
3. Calculamos los autovalores \(\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_d\) y sus correspondientes autovectores \(\mathbf{v}_1, \dots, \mathbf{v}_d\) de \(S\).
4. Los autovectores son las **componentes principales** (direcciones de máxima varianza). El primer autovector (asociado al mayor autovalor) es la dirección que maximiza la varianza de la proyección.
5. La varianza explicada por la componente \(i\) es \(\lambda_i / \sum_{j=1}^d \lambda_j\). Esto permite decidir cuántas componentes retener.

**Ejemplo con un pequeño dataset 2D:**

Supongamos datos: \((2,3), (3,4), (4,2), (5,3), (6,4)\). Centramos:
Medias: \(\bar{x} = (2+3+4+5+6)/5 = 4\), \(\bar{y} = (3+4+2+3+4)/5 = 3.2\).  
Datos centrados:
\[
\tilde{X} = \begin{pmatrix}
-2 & -0.2 \\
-1 & 0.8 \\
0 & -1.2 \\
1 & -0.2 \\
2 & 0.8
\end{pmatrix}
\]
Matriz de covarianza:
\[
S = \frac{1}{4} \tilde{X}^T \tilde{X} = \frac{1}{4} \begin{pmatrix}
(-2)^2+(-1)^2+0^2+1^2+2^2 & (-2)(-0.2)+(-1)(0.8)+0(-1.2)+1(-0.2)+2(0.8) \\
\text{simétrica} & (-0.2)^2+0.8^2+(-1.2)^2+(-0.2)^2+0.8^2
\end{pmatrix}
\]
Calculamos:
- Suma de cuadrados x: \(4+1+0+1+4 = 10\)
- Suma de productos: \(0.4 -0.8 +0 -0.2 +1.6 = 1.0\)
- Suma de cuadrados y: \(0.04+0.64+1.44+0.04+0.64 = 2.8\)
Entonces:
\[
S = \frac{1}{4} \begin{pmatrix} 10 & 1 \\ 1 & 2.8 \end{pmatrix} = \begin{pmatrix} 2.5 & 0.25 \\ 0.25 & 0.7 \end{pmatrix}
\]
Buscamos autovalores de \(S\):
\[
\det(S - \lambda I) = (2.5-\lambda)(0.7-\lambda) - 0.25^2 = 1.75 - 2.5\lambda -0.7\lambda + \lambda^2 - 0.0625 = \lambda^2 - 3.2\lambda + 1.6875 = 0
\]
Soluciones: \(\lambda = \frac{3.2 \pm \sqrt{3.2^2 - 4\cdot1.6875}}{2} = \frac{3.2 \pm \sqrt{10.24 - 6.75}}{2} = \frac{3.2 \pm \sqrt{3.49}}{2} = \frac{3.2 \pm 1.868}{2}\)
\(\lambda_1 \approx 2.534\), \(\lambda_2 \approx 0.666\). Varianza total = 3.2, primera componente explica 2.534/3.2 ≈ 79.2%.

Autovector para \(\lambda_1\): resolver \((S - \lambda_1 I)\mathbf{v}=0\):
\[
\begin{pmatrix} 2.5-2.534 & 0.25 \\ 0.25 & 0.7-2.534 \end{pmatrix} \approx \begin{pmatrix} -0.034 & 0.25 \\ 0.25 & -1.834 \end{pmatrix}
\]
De la primera ecuación: \(-0.034 v_1 + 0.25 v_2 = 0\) ⇒ \(v_2 \approx 0.136 v_1\). Tomando \(v_1=1\), \(v_2 \approx 0.136\). Normalizando, la primera componente principal es aproximadamente \((0.991, 0.135)\). Es casi horizontal, indicando que la mayor varianza está en la dirección x.

Las proyecciones de los datos sobre esta componente son \( \tilde{X} \cdot \mathbf{v}_1 \), que dan las nuevas coordenadas en 1D.

**Interpretación en ML:** PCA se usa para:
- Reducción de dimensionalidad antes de aplicar otros modelos.
- Visualización de datos de alta dimensión (proyectando a 2D o 3D).
- Eliminación de ruido (descartando componentes de baja varianza).
- Preprocesamiento para algoritmos que sufren la maldición de la dimensionalidad.

#### Deep Learning (DL)

##### 1. Estabilidad de dinámicas en RNNs

En redes neuronales recurrentes (RNNs), el estado oculto se actualiza como \(\mathbf{h}_t = \sigma(W \mathbf{h}_{t-1} + U \mathbf{x}_t + \mathbf{b})\). Durante el entrenamiento, los gradientes se propagan a través del tiempo. Si consideramos la parte lineal (ignorando la no linealidad y las entradas), la evolución es \(\mathbf{h}_t = W \mathbf{h}_{t-1}\). Después de \(T\) pasos, \(\mathbf{h}_T = W^T \mathbf{h}_0\). Los autovalores de \(W\) determinan el comportamiento:

- Si algún autovalor tiene módulo > 1, las componentes en esa dirección crecen exponencialmente (**gradiente explosivo**).
- Si todos tienen módulo < 1, las componentes decaen (**gradiente evanescente**).

Por eso, en la práctica se usan arquitecturas como LSTM o GRU que controlan el flujo de gradiente, y se inicializan las matrices de pesos de forma que los autovalores estén cerca de 1 (por ejemplo, inicialización identidad).

**Ejemplo:** Supongamos una RNN con peso recurrente \(W = \begin{pmatrix} 0.9 & 0 \\ 0 & 1.1 \end{pmatrix}\). El autovalor 1.1 causará explosión de gradientes si la secuencia es larga.

##### 2. Análisis de representaciones en transformers

En transformers, las matrices de atención y las matrices de pesos de las capas feed-forward pueden analizarse mediante su espectro de autovalores. Por ejemplo, el **rango efectivo** de las representaciones está relacionado con la rapidez con que decaen los autovalores de la matriz de covarianza de las activaciones. Un decaimiento lento indica que se necesitan muchas dimensiones para capturar la variabilidad; un decaimiento rápido sugiere que las representaciones son de bajo rango (redundantes).

Además, en **análisis de estabilidad** de transformers, se estudia cómo los autovalores de las matrices de atención afectan la propagación de información a través de las capas.

##### 3. Hessiana en optimización

En optimización, la matriz Hessiana \(H\) (segundas derivadas) de la función de pérdida contiene información sobre la curvatura. Sus autovalores indican:
- Si todos son positivos, el punto es un mínimo local.
- Si hay autovalores negativos, es un punto de silla.
- El cociente entre el mayor y menor autovalor (número de condición) afecta la velocidad de convergencia del gradiente descendente.

En deep learning, la Hessiana es enorme, pero se pueden estimar sus autovalores extremos para ajustar la tasa de aprendizaje o para diagnóstico.

##### 4. Descomposición espectral en redes neuronales

Algunas técnicas de regularización o compresión se basan en la descomposición espectral de las matrices de pesos. Por ejemplo, **Weight Normalization** reparametriza los pesos como \(\mathbf{w} = g \frac{\mathbf{v}}{\|\mathbf{v}\|}\), que es esencialmente usar la dirección del autovector principal. También en **SVD para compresión**, se reemplaza una matriz de pesos por su aproximación de bajo rango usando los mayores valores singulares (que son las raíces cuadradas de los autovalores de \(W^T W\)).

---
