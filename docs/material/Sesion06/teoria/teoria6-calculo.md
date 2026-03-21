## Semana 6: Transformaciones Lineales

### Teoría

#### 1. Definición de transformación lineal

Una **transformación lineal** \(T: \mathbb{R}^n \rightarrow \mathbb{R}^m\) es una función que asigna a cada vector \(\mathbf{x} \in \mathbb{R}^n\) un vector \(T(\mathbf{x}) \in \mathbb{R}^m\) tal que satisface dos propiedades:

1. **Aditividad:** \(T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})\) para todos \(\mathbf{u}, \mathbf{v} \in \mathbb{R}^n\).
2. **Homogeneidad:** \(T(\alpha \mathbf{u}) = \alpha T(\mathbf{u})\) para todo \(\mathbf{u} \in \mathbb{R}^n\) y \(\alpha \in \mathbb{R}\).

**Ejemplo:** La función \(T(x, y) = (2x, x + y, 3y)\) es lineal. Verifiquemos:

- \(T(\mathbf{u}+\mathbf{v}) = T(u_1+v_1, u_2+v_2) = (2(u_1+v_1), (u_1+v_1)+(u_2+v_2), 3(u_2+v_2))\)  
  \(= (2u_1+2v_1, u_1+u_2+v_1+v_2, 3u_2+3v_2)\)  
  \(= (2u_1, u_1+u_2, 3u_2) + (2v_1, v_1+v_2, 3v_2) = T(\mathbf{u}) + T(\mathbf{v})\)

- \(T(\alpha \mathbf{u}) = T(\alpha u_1, \alpha u_2) = (2\alpha u_1, \alpha u_1 + \alpha u_2, 3\alpha u_2) = \alpha (2u_1, u_1+u_2, 3u_2) = \alpha T(\mathbf{u})\)

**Contraejemplo:** La función \(T(x) = x^2\) no es lineal porque \(T(x+y) = (x+y)^2 \neq x^2 + y^2\) en general.

#### 2. Representación matricial

Toda transformación lineal \(T: \mathbb{R}^n \rightarrow \mathbb{R}^m\) puede representarse mediante una matriz \(A\) de tamaño \(m \times n\) tal que:

\[
T(\mathbf{x}) = A \mathbf{x}
\]

donde las columnas de \(A\) son las imágenes de los vectores de la base canónica:  
\(A = [T(\mathbf{e}_1) \; T(\mathbf{e}_2) \; \dots \; T(\mathbf{e}_n)]\).

**Ejemplo:** Para la transformación del ejemplo anterior \(T(x,y) = (2x, x+y, 3y)\):
- \(T(\mathbf{e}_1) = T(1,0) = (2, 1, 0)\)
- \(T(\mathbf{e}_2) = T(0,1) = (0, 1, 3)\)
Por tanto,
\[
A = \begin{pmatrix}
2 & 0 \\
1 & 1 \\
0 & 3
\end{pmatrix}
\]
Verificación: \(A \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 2x \\ x + y \\ 3y \end{pmatrix}\), correcto.

#### 3. Composición de transformaciones

Si tenemos dos transformaciones lineales \(T: \mathbb{R}^n \rightarrow \mathbb{R}^m\) y \(S: \mathbb{R}^m \rightarrow \mathbb{R}^p\), la composición \(S \circ T: \mathbb{R}^n \rightarrow \mathbb{R}^p\) está definida por \((S \circ T)(\mathbf{x}) = S(T(\mathbf{x}))\). Su matriz asociada es el producto de las matrices correspondientes:

\[
[S \circ T] = [S][T]
\]

**Ejemplo:** Sean \(T(x,y) = (x+y, 2x - y)\) y \(S(u,v) = (u - v, u + 2v)\). Primero hallamos matrices:
- \(T(1,0) = (1,2)\), \(T(0,1) = (1,-1)\) ⇒ \(A_T = \begin{pmatrix} 1 & 1 \\ 2 & -1 \end{pmatrix}\)
- \(S(1,0) = (1,1)\), \(S(0,1) = (-1,2)\) ⇒ \(A_S = \begin{pmatrix} 1 & -1 \\ 1 & 2 \end{pmatrix}\)

La composición \(S \circ T\) tiene matriz:
\[
A_S A_T = \begin{pmatrix} 1 & -1 \\ 1 & 2 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 2 & -1 \end{pmatrix} = \begin{pmatrix} 1\cdot1 + (-1)\cdot2 & 1\cdot1 + (-1)\cdot(-1) \\ 1\cdot1 + 2\cdot2 & 1\cdot1 + 2\cdot(-1) \end{pmatrix} = \begin{pmatrix} 1-2 & 1+1 \\ 1+4 & 1-2 \end{pmatrix} = \begin{pmatrix} -1 & 2 \\ 5 & -1 \end{pmatrix}
\]

Verificación: \((S \circ T)(x,y) = S(T(x,y)) = S(x+y, 2x-y) = ((x+y) - (2x-y), (x+y) + 2(2x-y)) = (x+y-2x+y, x+y+4x-2y) = (-x+2y, 5x - y)\), que coincide con la matriz obtenida.

#### 4. Tipos de transformaciones

##### Rotaciones (en ℝ²)
Una rotación de un ángulo \(\theta\) alrededor del origen tiene matriz:
\[
R_\theta = \begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{pmatrix}
\]
**Ejemplo:** Rotar \(\mathbf{x} = (2,1)\) un ángulo de \(90^\circ\) (\(\pi/2\)):
\[
R_{90^\circ} = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}, \quad
R_{90^\circ} \begin{pmatrix} 2 \\ 1 \end{pmatrix} = \begin{pmatrix} -1 \\ 2 \end{pmatrix}
\]

##### Escalados
Un escalado (dilatación/contracción) a lo largo de los ejes:
\[
S = \begin{pmatrix}
s_x & 0 \\
0 & s_y
\end{pmatrix}
\]
**Ejemplo:** Escalar \(\mathbf{x} = (2,3)\) con \(s_x = 2, s_y = 0.5\):
\[
S \begin{pmatrix} 2 \\ 3 \end{pmatrix} = \begin{pmatrix} 4 \\ 1.5 \end{pmatrix}
\]

##### Proyecciones
Proyección ortogonal sobre el eje x (en ℝ²):
\[
P_x = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}
\]
Proyección sobre una recta con dirección unitaria \(\mathbf{u}\) (vector columna): \(P = \mathbf{u} \mathbf{u}^T\).

**Ejemplo:** Proyectar \(\mathbf{x} = (3,4)\) sobre el eje x:
\[
P_x \begin{pmatrix} 3 \\ 4 \end{pmatrix} = \begin{pmatrix} 3 \\ 0 \end{pmatrix}
\]

#### 5. Interpretación de capas de redes como transformaciones

En una red neuronal, cada capa lineal (fully connected) realiza una transformación lineal seguida de una no linealidad (activación). La parte lineal es:

\[
\mathbf{h} = W \mathbf{x} + \mathbf{b}
\]

Esto es una **transformación afín** (lineal más traslación). Si ignoramos el sesgo o lo incluimos aumentando la dimensión, es una transformación lineal en un espacio aumentado. Las capas sucesivas son composiciones de estas transformaciones (afines) intercaladas con no linealidades.

Por ejemplo, una red de dos capas:
\[
\mathbf{h}_1 = \sigma(W_1 \mathbf{x} + \mathbf{b}_1), \quad
\mathbf{y} = \sigma(W_2 \mathbf{h}_1 + \mathbf{b}_2)
\]
La composición de las partes lineales (sin activación) sería \(W_2 (W_1 \mathbf{x} + \mathbf{b}_1) + \mathbf{b}_2 = (W_2 W_1) \mathbf{x} + (W_2 \mathbf{b}_1 + \mathbf{b}_2)\), que es nuevamente una transformación afín. Por eso las no linealidades son esenciales para aumentar la capacidad expresiva.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Feature engineering (transformaciones de características)

A menudo aplicamos transformaciones lineales a los datos para mejorar el rendimiento de los modelos. Por ejemplo, **escalado de características** (normalización) es una transformación lineal (aunque a veces afín) que lleva cada característica a un rango similar. La estandarización (z-score) es:

\[
x' = \frac{x - \mu}{\sigma}
\]
que es una transformación afín. En forma matricial, para todo el dataset \(X\) (cada columna es una característica), la estandarización se escribe como \(X' = (X - \mathbf{1}\boldsymbol{\mu}^T) \text{diag}(1/\boldsymbol{\sigma})\).

Otro ejemplo: **PCA** es una transformación lineal (rotación + proyección) que lleva los datos a un nuevo sistema de coordenadas donde las componentes están ordenadas por varianza.

##### 2. Regresión lineal (transformación lineal)

La regresión lineal modela la relación entre entrada y salida como una transformación lineal (afín):
\[
\hat{y} = \mathbf{w}^T \mathbf{x} + b
\]
En forma matricial para todo el dataset: \(\hat{\mathbf{y}} = X \mathbf{w} + b\). Es una transformación lineal de las características a la salida.

##### 3. SVM con kernel (mapeo a espacio de características)

El truco del kernel en SVM consiste en mapear los datos a un espacio de mayor dimensión mediante una transformación \(\phi(\mathbf{x})\), donde el producto punto en ese espacio se puede calcular mediante una función kernel \(K(\mathbf{x}, \mathbf{x}') = \phi(\mathbf{x}) \cdot \phi(\mathbf{x}')\). Aunque \(\phi\) puede ser no lineal, la idea es que en el nuevo espacio la separación sea lineal. Ejemplo: el kernel polinomial de grado 2 para \(\mathbf{x} \in \mathbb{R}^2\):

\[
\phi(x_1, x_2) = (x_1^2, x_2^2, \sqrt{2} x_1 x_2, x_1, x_2, 1)
\]
Este mapeo es una transformación no lineal de \(\mathbb{R}^2\) a \(\mathbb{R}^6\), pero una vez en ese espacio, la SVM realiza una transformación lineal (el hiperplano).

#### Deep Learning (DL)

##### 1. Capas lineales (fully connected)

Cada capa lineal en una red neuronal es una transformación afín. Por ejemplo, en un clasificador de imágenes, la primera capa toma un vector aplanado de píxeles y aplica:

\[
\mathbf{h} = W \mathbf{x} + \mathbf{b}
\]
donde \(W\) es la matriz de pesos que se aprende. Esta transformación puede verse como una proyección (combinación lineal) de las características de entrada a un nuevo espacio de representación.

**Ejemplo concreto:** Una capa que reduce dimensionalidad de 784 (MNIST) a 256:
\[
W \in \mathbb{R}^{256 \times 784}, \quad \mathbf{b} \in \mathbb{R}^{256}
\]
La operación \(W\mathbf{x}\) es una transformación lineal que mezcla todas las características de entrada.

##### 2. Redes profundas como composición de transformaciones

Una red profunda compone muchas transformaciones lineales (con activaciones no lineales entre ellas). Cada capa aprende una representación intermedia. Por ejemplo, en una red convolucional, las primeras capas aprenden bordes y texturas (transformaciones locales), y las últimas capas aprenden conceptos de alto nivel.

Matemáticamente, la salida de la red (sin la última activación) es una composición de funciones afines:
\[
f(\mathbf{x}) = W_L \sigma(W_{L-1} \sigma(\cdots \sigma(W_1 \mathbf{x} + \mathbf{b}_1) \cdots) + \mathbf{b}_{L-1}) + \mathbf{b}_L
\]
Sin las no linealidades, sería simplemente una única transformación lineal (el producto de todas las matrices), pero la presencia de activaciones permite modelar relaciones no lineales complejas.

##### 3. Kernel en CNN (convolución como transformación lineal)

La operación de convolución en una CNN es también una transformación lineal. Para una imagen de entrada, la convolución con un kernel produce un mapa de características. Puede representarse como una multiplicación de una matriz (que depende del kernel) con el vector de píxeles. La matriz es una matriz de Toeplitz por bloques (o matriz circulante) que aplica la misma transformación localmente en toda la imagen.

**Ejemplo:** Una convolución 1D con kernel \(k = (k_1, k_2, k_3)\) sobre una señal \(\mathbf{x} = (x_1, x_2, x_3, x_4)\) (con padding adecuado) puede escribirse como:

\[
\mathbf{y} = \begin{pmatrix}
k_1 & k_2 & k_3 & 0 \\
0 & k_1 & k_2 & k_3
\end{pmatrix} \mathbf{x}
\]
Esto es una transformación lineal. En 2D, la matriz es más compleja pero sigue siendo lineal.

##### 4. Compresión y representación de audio, imágenes, video y datos

Muchas técnicas de compresión y representación se basan en transformaciones lineales. Por ejemplo:

- **JPEG:** Usa la Transformada Discreta del Coseno (DCT), que es una transformación lineal ortogonal, para representar bloques de imagen en el dominio de la frecuencia. Los coeficientes de alta frecuencia se cuantizan agresivamente (pérdida).
- **MP3:** Similar, usa la Transformada de Fourier Modificada (MDCT) para audio.
- **Autoencoders lineales:** Un autoencoder lineal (sin activaciones no lineales) equivale a PCA, que es una transformación lineal de los datos a un espacio de menor dimensión y luego la inversa (otra transformación lineal) para reconstruir.

En representaciones de datos, a menudo se aplican transformaciones lineales para reducir dimensionalidad (PCA, SVD) o para hacer los datos más adecuados para un modelo (whitening, normalización).

**Ejemplo PCA:** Dada una matriz de datos \(X\) (centrada), la transformación a componentes principales es:
\[
Z = X V
\]
donde \(V\) es la matriz de autovectores de la covarianza. Esto es una rotación (ortogonal) que alinea los ejes con las direcciones de máxima varianza. Luego, para reducir dimensionalidad, se toman solo las primeras \(k\) columnas de \(Z\) (proyección).

---

