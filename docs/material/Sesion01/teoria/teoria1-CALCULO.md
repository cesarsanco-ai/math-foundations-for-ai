# Semana 1: Fundamentos Matemáticos

## Teoría

### 1. Notación matemática

#### Índices
Los índices se utilizan para referirse a elementos de una secuencia, conjunto o estructura de datos. Se denotan típicamente con subíndices: \(x_1, x_2, x_3, \dots, x_n\).

**Ejemplo paso a paso:**  
Consideremos las calificaciones de 5 estudiantes: 15, 18, 14, 20, 16.  
Podemos denotar: \(x_1 = 15\), \(x_2 = 18\), \(x_3 = 14\), \(x_4 = 20\), \(x_5 = 16\).  
Para referirnos al tercer elemento: \(x_3 = 14\).

#### Sucesiones
Una sucesión es una función cuyo dominio son los números naturales. Se denota \(\{a_n\}_{n=1}^{\infty}\).

**Ejemplo:** \(a_n = \frac{1}{n}\) produce: \(1, \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \dots\)

#### Series
Una serie es la suma de los términos de una sucesión: \(\sum_{n=1}^{\infty} a_n\).

**Ejemplo:** Serie geométrica: \(\sum_{n=0}^{\infty} r^n = \frac{1}{1-r}\) para \(|r| < 1\).

#### Sumatorias simples
La sumatoria simple suma una secuencia de términos:

\[\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n\]

**Ejemplo paso a paso:**  
Calcular \(\sum_{i=1}^{4} i^2\):
- \(i=1\): \(1^2 = 1\)
- \(i=2\): \(2^2 = 4\)
- \(i=3\): \(3^2 = 9\)
- \(i=4\): \(4^2 = 16\)
Suma total: \(1 + 4 + 9 + 16 = 30\)

#### Sumatorias dobles
Se utilizan para recorrer dos índices, típicamente filas y columnas de una matriz:

\[\sum_{i=1}^{m} \sum_{j=1}^{n} a_{ij}\]

**Ejemplo paso a paso:**  
Dada la matriz \(A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{pmatrix}\), calcular \(\sum_{i=1}^{2} \sum_{j=1}^{3} a_{ij}\):
- \(i=1, j=1\): 1
- \(i=1, j=2\): 2
- \(i=1, j=3\): 3
- \(i=2, j=1\): 4
- \(i=2, j=2\): 5
- \(i=2, j=3\): 6
Suma total: \(1+2+3+4+5+6 = 21\)

#### Sumatorias triples
Aparecen en problemas con tres dimensiones, como tensores:

\[\sum_{i=1}^{l} \sum_{j=1}^{m} \sum_{k=1}^{n} a_{ijk}\]

#### Productorias
Similar a las sumatorias, pero multiplicando:

\[\prod_{i=1}^{n} x_i = x_1 \cdot x_2 \cdots x_n\]

**Ejemplo:** \(\prod_{i=1}^{4} i = 1 \cdot 2 \cdot 3 \cdot 4 = 24\)

### 2. Sistemas de dimensiones

#### 2D (bidimensional)
Un sistema 2D tiene dos ejes coordenados (x, y). Ejemplos: puntos en un plano, imágenes en escala de grises (alto × ancho).

**Ejemplo:** El punto \(P = (3, 4)\) está a 3 unidades en el eje x y 4 en el eje y.

#### 3D (tridimensional)
Añade un tercer eje z. Ejemplos: puntos en el espacio, videos (frames, alto, ancho), imágenes a color (alto, ancho, canales RGB).

**Ejemplo:** El punto \(P = (1, 2, 3)\) en el espacio 3D.

#### n-dimensional
Generalización a n dimensiones. Un punto se representa como \((x_1, x_2, \dots, x_n)\). En IA, cada punto es una observación con n características (features).

**Ejemplo:** Un paciente con edad, peso, altura, presión sistólica y diastólica → \( \text{paciente} = (45, 70, 1.75, 120, 80) \) en \(\mathbb{R}^5\).

### 3. Estructura de datos: Grafos

Un grafo es un conjunto de nodos (vértices) conectados por aristas. Se denota \(G = (V, E)\).

- **V**: conjunto de vértices
- **E**: conjunto de aristas (pares de vértices)

**Ejemplo:** Red social: personas como nodos, amistades como aristas.

**Tipos:**
- **Dirigido:** las aristas tienen dirección (ej: Twitter, sigues a alguien).
- **No dirigido:** las aristas no tienen dirección (ej: Facebook, amistad mutua).

**Aplicación en IA:** Los grafos se usan en redes neuronales de grafos (GNN), sistemas de recomendación, análisis de redes sociales, etc.

### 4. Objetos matemáticos

#### Escalares
Un número real o complejo. Denotado por letras sin negrita: \(a, b, c, \alpha, \beta\).

**Ejemplo:** \(x = 5\), \(\lambda = 0.01\) (learning rate en ML).

#### Vectores
Lista ordenada de números. Se denotan con negrita: \(\mathbf{v} = (v_1, v_2, \dots, v_n)\) o \(\vec{v}\).

**Ejemplo:** \(\mathbf{v} = [2, -1, 4]\) en \(\mathbb{R}^3\).

En ML, un vector representa una observación: \(\mathbf{x}^{(i)} = [x_1^{(i)}, x_2^{(i)}, \dots, x_n^{(i)}]\) son las características del i-ésimo ejemplo.

#### Matrices
Tabla rectangular de números con filas y columnas. Se denotan con mayúsculas: \(A, B, W\).

\[
A = \begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{pmatrix}
\]

**Ejemplo:** \(W = \begin{pmatrix} 0.2 & -0.5 \\ 0.8 & 0.1 \end{pmatrix}\) podría ser una matriz de pesos en una red neuronal.

#### Tensores
Generalización de vectores y matrices a más dimensiones. Un tensor de orden (rank) 0 es un escalar, orden 1 es un vector, orden 2 es una matriz, orden 3 o más es un tensor.

**Ejemplo:** Una imagen a color de 224×224 píxeles se representa como un tensor 3D: (224, 224, 3). Un lote (batch) de 32 imágenes es un tensor 4D: (32, 224, 224, 3).

### 5. Funciones elementales

#### Función lineal
\(f(x) = mx + b\)

**Ejemplo paso a paso:**  
\(f(x) = 2x + 1\)  
- \(x = 0 \Rightarrow f(0) = 1\)  
- \(x = 1 \Rightarrow f(1) = 3\)  
- \(x = -1 \Rightarrow f(-1) = -1\)

**Aplicación:** Modelos de regresión lineal.

#### Función polinomial
\(f(x) = a_n x^n + a_{n-1} x^{n-1} + \cdots + a_1 x + a_0\)

**Ejemplo:** \(f(x) = x^2 - 3x + 2\)  
- \(x = 0 \Rightarrow f(0) = 2\)  
- \(x = 1 \Rightarrow f(1) = 0\)  
- \(x = 2 \Rightarrow f(2) = 0\) (raíces)

#### Función exponencial
\(f(x) = a^x\) con \(a > 0\), \(a \neq 1\). La base más común es \(e\) (número de Euler ≈ 2.71828).

**Ejemplo:** \(f(x) = e^x\)  
- \(x = 0 \Rightarrow f(0) = 1\)  
- \(x = 1 \Rightarrow f(1) \approx 2.718\)  
- \(x = -1 \Rightarrow f(-1) \approx 0.368\)

**Aplicación:** Crecimiento poblacional, interés compuesto, kernel RBF en SVM: \(K(x, x') = \exp(-\gamma \|x - x'\|^2)\).

#### Función logarítmica
\(f(x) = \log_a x\) con \(a > 0\), \(a \neq 1\), \(x > 0\). Es la inversa de la exponencial.

**Ejemplo:** \(\log_{10} 100 = 2\) porque \(10^2 = 100\).  
\(\ln e = 1\) porque \(e^1 = e\).

**Aplicación:** Entropía, log-loss, verosimilitud.

#### Función trigonométrica
- Seno: \(f(x) = \sin x\)
- Coseno: \(f(x) = \cos x\)

**Ejemplo:** \(\sin 0 = 0\), \(\sin \pi/2 = 1\), \(\cos 0 = 1\), \(\cos \pi = -1\).

**Aplicación:** Positional encoding en Transformers:  
\(PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d}}\right)\),  
\(PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d}}\right)\).

#### Función trigonométrica hiperbólica
- Seno hiperbólico: \(\sinh x = \frac{e^x - e^{-x}}{2}\)
- Coseno hiperbólico: \(\cosh x = \frac{e^x + e^{-x}}{2}\)
- Tangente hiperbólica: \(\tanh x = \frac{\sinh x}{\cosh x} = \frac{e^x - e^{-x}}{e^x + e^{-x}}\)

**Ejemplo:** \(\tanh 0 = 0\), \(\tanh 1 \approx 0.762\), \(\tanh 2 \approx 0.964\).

**Aplicación:** Función de activación tanh en RNNs y MLPs.

### 6. Tipos de funciones por dominio

#### Composición de funciones
Dadas \(f\) y \(g\), la composición \(f \circ g\) se define como \((f \circ g)(x) = f(g(x))\).

**Ejemplo paso a paso:**  
\(f(x) = x^2\), \(g(x) = 2x + 1\)  
\((f \circ g)(x) = f(g(x)) = f(2x+1) = (2x+1)^2\)  
- Si \(x = 1\): \(g(1) = 3\), \(f(3) = 9\)  
- Directo: \((2\cdot1+1)^2 = 9\) ✓

**Aplicación en DL:** Una red neuronal es una composición de funciones:  
\(f(x) = f_L(f_{L-1}(\dots f_1(x)\dots))\), donde cada capa aplica una transformación lineal seguida de una activación no lineal.

#### Funciones por tramos
Definidas por diferentes expresiones en diferentes intervalos.

**Ejemplo:** ReLU (Rectified Linear Unit):
\[
\text{ReLU}(x) = 
\begin{cases} 
x & \text{si } x \geq 0 \\
0 & \text{si } x < 0
\end{cases}
\]

**Aplicación:** Función de activación más usada en DL.

### 7. Funciones de activación

#### Sigmoide
\[
\sigma(x) = \frac{1}{1 + e^{-x}}
\]

**Ejemplo paso a paso:**  
- \(x = 0\): \(\sigma(0) = \frac{1}{1 + e^0} = \frac{1}{1+1} = 0.5\)  
- \(x = 2\): \(\sigma(2) = \frac{1}{1 + e^{-2}} \approx \frac{1}{1 + 0.1353} \approx 0.881\)  
- \(x = -2\): \(\sigma(-2) = \frac{1}{1 + e^{2}} \approx \frac{1}{1 + 7.389} \approx 0.119\)

**Aplicación:** Regresión logística (salida entre 0 y 1), compuertas en LSTM.

#### Tanh
\[
\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}
\]

**Ejemplo paso a paso:**  
- \(x = 0\): \(\tanh(0) = 0\)  
- \(x = 1\): \(\tanh(1) \approx \frac{2.718 - 0.368}{2.718 + 0.368} = \frac{2.35}{3.086} \approx 0.762\)  
- \(x = -1\): \(\tanh(-1) \approx -0.762\)

**Aplicación:** Función de activación en RNNs, centrada en cero.

#### ReLU
\[
\text{ReLU}(x) = \max(0, x)
\]

**Ejemplo paso a paso:**  
- \(x = 3\): ReLU(3) = 3  
- \(x = -2\): ReLU(-2) = 0  
- \(x = 0\): ReLU(0) = 0

**Aplicación:** Función de activación por defecto en CNN y MLP.

### 8. Concepto de función de pérdida

Una función de pérdida \(L(y, \hat{y})\) mide la discrepancia entre el valor real \(y\) y el valor predicho \(\hat{y}\).

#### Definición general
\[
L(\theta) = \frac{1}{n} \sum_{i=1}^{n} \ell(y_i, \hat{y}_i)
\]
donde \(\ell\) es la pérdida por ejemplo, y \(\theta\) son los parámetros del modelo.

#### Ejemplos intuitivos

**Distancia entre números (regresión):** Error cuadrático medio
\[
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
\]

**Diferencia entre probabilidades (clasificación):** Entropía cruzada
\[
\text{Cross-Entropy} = -\sum_{i=1}^{n} y_i \log(\hat{y}_i)
\]
donde \(y_i \in \{0,1\}\) y \(\hat{y}_i \in [0,1]\) es la probabilidad predicha.

**Ejemplo paso a paso (MSE):**  
Valores reales: \(y = [3, -0.5, 2, 7]\)  
Predicciones: \(\hat{y} = [2.5, 0.0, 2, 8]\)  
Diferencias: \([0.5, -0.5, 0, -1]\)  
Cuadrados: \([0.25, 0.25, 0, 1]\)  
Suma: \(1.5\)  
MSE = \(1.5 / 4 = 0.375\)

**Ejemplo paso a paso (Cross-Entropy):**  
Clasificación binaria, \(y = 1\), \(\hat{y} = 0.8\)  
Pérdida: \(-\log(0.8) \approx -(-0.223) = 0.223\)  
Si \(y = 0\), \(\hat{y} = 0.1\): pérdida \(-\log(0.9) \approx 0.105\) (notar que para \(y=0\) usamos \(-\log(1-\hat{y})\))

---

## Aplicaciones prácticas

### Machine Learning (ML)

#### Regresión lineal (función lineal)
Modelo: \(\hat{y} = w^T x + b\)  
Es una función lineal de las características \(x\). Los parámetros \(w\) (pesos) y \(b\) (sesgo) se aprenden minimizando una función de pérdida como MSE.

**Ecuación:**  
\[
\hat{y} = \sum_{j=1}^{n} w_j x_j + b
\]
Aquí aparece una **sumatoria** (tema de la semana) sobre las características.

#### Regresión logística (sigmoide, softmax)
Modelo de clasificación binaria:  
\[
P(y=1|x) = \sigma(w^T x + b) = \frac{1}{1 + e^{-(w^T x + b)}}
\]
La **función sigmoide** transforma una combinación lineal en una probabilidad entre 0 y 1.

Para clasificación multiclase, se usa **softmax**:  
\[
P(y=k|x) = \frac{e^{w_k^T x + b_k}}{\sum_{j=1}^{K} e^{w_j^T x + b_j}}
\]
Aquí aparecen **exponenciales** y una **sumatoria** en el denominador.

#### SVM (kernel RBF: exponencial)
El kernel RBF (Radial Basis Function) mide similitud entre dos puntos:
\[
K(x, x') = \exp\left(-\gamma \|x - x'\|^2\right)
\]
Es una **función exponencial** aplicada a una distancia.

#### Entropía (logaritmo)
La entropía mide la incertidumbre en una distribución de probabilidad:
\[
H(S) = -\sum_{i=1}^{n} p_i \log_2 p_i
\]
Aparece una **sumatoria** y un **logaritmo**. En árboles de decisión, se usa para medir la impureza.

#### Funciones de pérdida (log-loss)
La log-loss (entropía cruzada binaria) es:
\[
L = -\frac{1}{n} \sum_{i=1}^{n} \left[ y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i) \right]
\]
Combina **sumatoria** y **logaritmo**.

### Deep Learning (DL)

#### Perceptrón (función lineal + activación)
Un perceptrón es la unidad básica de una red neuronal:
\[
\text{salida} = f(w^T x + b)
\]
donde \(f\) es una función de activación (ReLU, sigmoide, tanh). Aquí se combina una **función lineal** (suma ponderada) con una **función no lineal**.

#### Funciones de activación (ReLU, GELU)
- ReLU: \( \max(0, x) \) (función por tramos)
- GELU: \( x \cdot \Phi(x) \) donde \(\Phi\) es la CDF de la normal, aproximada como \(0.5x(1 + \tanh(\sqrt{2/\pi}(x + 0.044715x^3)))\) (combina polinomio, exponencial y tanh).

#### Positional encoding (seno/coseno)
En Transformers, se añade información de posición:
\[
PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d}}\right), \quad PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d}}\right)
\]
Son **funciones trigonométricas** aplicadas a la posición.

#### RNN (tanh, sigmoide)
En una RNN, el estado oculto se actualiza como:
\[
h_t = \tanh(W_{hh} h_{t-1} + W_{xh} x_t + b_h)
\]
Aparece la **función tanh** (o sigmoide en LSTMs).

#### Atención (softmax)
El mecanismo de atención calcula pesos normalizados:
\[
\alpha_{ij} = \frac{\exp(e_{ij})}{\sum_{k} \exp(e_{ik})}
\]
donde \(e_{ij}\) son puntuaciones de atención. Aquí se usa **exponencial** y **sumatoria** (softmax).

---
