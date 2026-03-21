## Semana 8: Descomposición de Matrices (SVD)

### Teoría

#### 1. Descomposición en Valores Singulares (SVD)

La **descomposición en valores singulares** (Singular Value Decomposition, SVD) es una de las factorizaciones matriciales más importantes y poderosas. Para cualquier matriz \(A\) de tamaño \(m \times n\) (con \(m\) filas y \(n\) columnas), existen matrices \(U\), \(\Sigma\) y \(V\) tales que:

\[
A = U \Sigma V^T
\]

donde:
- \(U\) es una matriz ortogonal de \(m \times m\) (\(U^T U = I_m\)). Sus columnas se llaman **vectores singulares izquierdos**.
- \(V\) es una matriz ortogonal de \(n \times n\) (\(V^T V = I_n\)). Sus columnas se llaman **vectores singulares derechos**.
- \(\Sigma\) es una matriz diagonal de \(m \times n\) con elementos no negativos \(\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_r \geq 0\) en la diagonal principal, donde \(r = \text{rango}(A)\). Estos \(\sigma_i\) son los **valores singulares**. El resto de entradas son cero.

**Ejemplo:** Para una matriz \(A\) de \(2 \times 2\), la SVD tiene la forma:
\[
A = \begin{pmatrix} u_{11} & u_{12} \\ u_{21} & u_{22} \end{pmatrix}
\begin{pmatrix} \sigma_1 & 0 \\ 0 & \sigma_2 \end{pmatrix}
\begin{pmatrix} v_{11} & v_{21} \\ v_{12} & v_{22} \end{pmatrix}
\]
Observa que \(V^T\) tiene las filas como los vectores singulares derechos transpuestos.

**Cálculo de la SVD (concepto):** Los valores singulares son las raíces cuadradas de los autovalores de \(A^T A\) (o de \(A A^T\)). Los vectores singulares derechos \(V\) son los autovectores de \(A^T A\), y los vectores singulares izquierdos \(U\) son los autovectores de \(A A^T\). Las matrices \(U\) y \(V\) están ordenadas de modo que el primer vector singular corresponde al mayor valor singular.

**Ejemplo numérico paso a paso:**  
Sea \(A = \begin{pmatrix} 3 & 0 \\ 4 & 5 \end{pmatrix}\). Primero calculamos \(A^T A\):
\[
A^T A = \begin{pmatrix} 3 & 4 \\ 0 & 5 \end{pmatrix} \begin{pmatrix} 3 & 0 \\ 4 & 5 \end{pmatrix} = \begin{pmatrix} 9+16 & 0+20 \\ 0+20 & 0+25 \end{pmatrix} = \begin{pmatrix} 25 & 20 \\ 20 & 25 \end{pmatrix}
\]
Autovalores de \(A^T A\): \(\det\begin{pmatrix} 25-\lambda & 20 \\ 20 & 25-\lambda \end{pmatrix} = (25-\lambda)^2 - 400 = \lambda^2 - 50\lambda + 625 - 400 = \lambda^2 - 50\lambda + 225 = 0\).  
Soluciones: \(\lambda = \frac{50 \pm \sqrt{2500 - 900}}{2} = \frac{50 \pm \sqrt{1600}}{2} = \frac{50 \pm 40}{2}\) ⇒ \(\lambda_1 = 45\), \(\lambda_2 = 5\).  
Los valores singulares son \(\sigma_1 = \sqrt{45} \approx 6.708\), \(\sigma_2 = \sqrt{5} \approx 2.236\).

Ahora los autovectores de \(A^T A\):
- Para \(\lambda_1=45\): \((25-45)x + 20y = 0\) ⇒ \(-20x + 20y = 0\) ⇒ \(x = y\). Autovector normalizado: \(\mathbf{v}_1 = (1/\sqrt{2}, 1/\sqrt{2}) \approx (0.7071, 0.7071)\).
- Para \(\lambda_2=5\): \((25-5)x + 20y = 0\) ⇒ \(20x + 20y = 0\) ⇒ \(x = -y\). Autovector normalizado: \(\mathbf{v}_2 = (1/\sqrt{2}, -1/\sqrt{2}) \approx (0.7071, -0.7071)\).

Así, \(V = \begin{pmatrix} 0.7071 & 0.7071 \\ 0.7071 & -0.7071 \end{pmatrix}\). Nota que las columnas son los autovectores. Entonces \(V^T = \begin{pmatrix} 0.7071 & 0.7071 \\ 0.7071 & -0.7071 \end{pmatrix}\) (en este caso es igual porque es simétrica).

Ahora calculamos \(U\) a partir de \(A V\). Sabemos que \(A V = U \Sigma\). Entonces \(A V\) tendrá columnas proporcionales a los vectores singulares izquierdos:
\[
A V = \begin{pmatrix} 3 & 0 \\ 4 & 5 \end{pmatrix} \begin{pmatrix} 0.7071 & 0.7071 \\ 0.7071 & -0.7071 \end{pmatrix} = \begin{pmatrix} 3\cdot0.7071 + 0\cdot0.7071 & 3\cdot0.7071 + 0\cdot(-0.7071) \\ 4\cdot0.7071 + 5\cdot0.7071 & 4\cdot0.7071 + 5\cdot(-0.7071) \end{pmatrix}
\]
\[
= \begin{pmatrix} 2.1213 & 2.1213 \\ (2.8284+3.5355) = 6.3639 & (2.8284 - 3.5355) = -0.7071 \end{pmatrix} = \begin{pmatrix} 2.1213 & 2.1213 \\ 6.3639 & -0.7071 \end{pmatrix}
\]
Ahora normalizamos las columnas para obtener \(U\):
- Primera columna: norma \(\sqrt{2.1213^2 + 6.3639^2} = \sqrt{4.5 + 40.5} = \sqrt{45} = \sigma_1\). Efectivamente, la norma es \(\sigma_1\). El vector unitario es \(\mathbf{u}_1 = (2.1213/\sigma_1, 6.3639/\sigma_1) = (2.1213/6.708, 6.3639/6.708) \approx (0.3162, 0.9487)\).
- Segunda columna: norma \(\sqrt{2.1213^2 + (-0.7071)^2} = \sqrt{4.5 + 0.5} = \sqrt{5} = \sigma_2\). Vector unitario: \(\mathbf{u}_2 = (2.1213/2.236, -0.7071/2.236) \approx (0.9487, -0.3162)\).

Por tanto,
\[
U \approx \begin{pmatrix} 0.3162 & 0.9487 \\ 0.9487 & -0.3162 \end{pmatrix}, \quad
\Sigma = \begin{pmatrix} 6.708 & 0 \\ 0 & 2.236 \end{pmatrix}, \quad
V^T = \begin{pmatrix} 0.7071 & 0.7071 \\ 0.7071 & -0.7071 \end{pmatrix}
\]
Verificación: \(U \Sigma V^T\) debe dar \(A\). (Se puede comprobar que el producto es aproximadamente \(A\)).

#### 2. Interpretación geométrica

La SVD descompone cualquier transformación lineal (representada por \(A\)) en tres pasos geométricos simples:

1. **Rotación/reflexión** (por \(V^T\)): lleva los vectores de la base canónica a los ejes principales de la transformación.
2. **Escalado** (por \(\Sigma\)): estira o encoge a lo largo de esos ejes según los valores singulares.
3. **Otra rotación/reflexión** (por \(U\)): lleva los ejes escalados al espacio de salida.

En términos de la acción sobre un vector \(\mathbf{x}\):
\[
A \mathbf{x} = U (\Sigma (V^T \mathbf{x}))
\]

Si consideramos la esfera unitaria en \(\mathbb{R}^n\), su imagen bajo \(A\) es un elipsoide en \(\mathbb{R}^m\) cuyos semiejes tienen longitudes \(\sigma_i\) y direcciones dadas por las columnas de \(U\). Los vectores singulares derechos \(V\) indican las direcciones en el espacio de entrada que son mapeadas a esos semiejes.

**Ejemplo visual:** Para \(A\) diagonal, la SVD es trivial: \(U\) y \(V\) son identidades, y \(\Sigma\) contiene los factores de escala. Para una matriz de rotación pura, los valores singulares son 1 y \(U\) y \(V\) son las matrices de rotación.

#### 3. Pseudoinversa de Moore–Penrose

La pseudoinversa de una matriz \(A\) (denotada \(A^+\)) generaliza el concepto de inversa para matrices no cuadradas o singulares. Se define mediante la SVD:

\[
A^+ = V \Sigma^+ U^T
\]
donde \(\Sigma^+\) se obtiene tomando la transpuesta de \(\Sigma\) y reemplazando cada valor singular no nulo \(\sigma_i\) por su recíproco \(1/\sigma_i\), dejando los ceros como cero.

**Propiedades:**
- Si \(A\) es cuadrada e invertible, \(A^+ = A^{-1}\).
- \(A A^+ A = A\), \(A^+ A A^+ = A^+\).
- Proporciona la solución de mínimos cuadrados de norma mínima para sistemas lineales: \(\mathbf{x} = A^+ \mathbf{b}\) minimiza \(\|A\mathbf{x} - \mathbf{b}\|^2\) y, entre las soluciones que minimizan, tiene la menor norma.

**Ejemplo:** Para \(A = \begin{pmatrix} 3 & 0 \\ 4 & 5 \end{pmatrix}\) del ejemplo anterior, \(\Sigma^+\) sería \(\begin{pmatrix} 1/6.708 & 0 \\ 0 & 1/2.236 \\ 0 & 0 \end{pmatrix}\) (si \(A\) fuera \(2 \times 2\), pero en realidad \(\Sigma\) es \(2 \times 2\), así que \(\Sigma^+\) es \(2 \times 2\) con los recíprocos). Entonces:
\[
A^+ = V \Sigma^+ U^T = \begin{pmatrix} 0.7071 & 0.7071 \\ 0.7071 & -0.7071 \end{pmatrix}
\begin{pmatrix} 0.1491 & 0 \\ 0 & 0.4472 \end{pmatrix}
\begin{pmatrix} 0.3162 & 0.9487 \\ 0.9487 & -0.3162 \end{pmatrix}
\]
Calculando se obtiene la pseudoinversa. En la práctica, se usa para resolver sistemas sobredeterminados.

#### 4. Aproximaciones de bajo rango

La SVD proporciona la mejor aproximación de rango \(k\) de una matriz \(A\) en el sentido de minimizar la norma de Frobenius (o la norma espectral). Esto es el **teorema de Eckart-Young**: si truncamos la SVD manteniendo solo los \(k\) mayores valores singulares, obtenemos la matriz de rango \(k\) que minimiza \(\|A - \hat{A}\|_F\).

Es decir, si escribimos:
\[
A = \sum_{i=1}^{r} \sigma_i \mathbf{u}_i \mathbf{v}_i^T
\]
entonces la aproximación de rango \(k\) es:
\[
A_k = \sum_{i=1}^{k} \sigma_i \mathbf{u}_i \mathbf{v}_i^T
\]
y se cumple que \(\|A - A_k\|_F = \sqrt{\sum_{i=k+1}^{r} \sigma_i^2}\).

**Ejemplo:** Con la matriz anterior, si tomamos solo el primer valor singular (k=1):
\[
A_1 = \sigma_1 \mathbf{u}_1 \mathbf{v}_1^T = 6.708 \cdot \begin{pmatrix} 0.3162 \\ 0.9487 \end{pmatrix} \begin{pmatrix} 0.7071 & 0.7071 \end{pmatrix}
\]
Calculamos: \(\mathbf{u}_1 \mathbf{v}_1^T = \begin{pmatrix} 0.3162 \\ 0.9487 \end{pmatrix} (0.7071, 0.7071) = \begin{pmatrix} 0.2236 & 0.2236 \\ 0.6708 & 0.6708 \end{pmatrix}\). Multiplicando por 6.708: \(A_1 \approx \begin{pmatrix} 1.5 & 1.5 \\ 4.5 & 4.5 \end{pmatrix}\). Comparado con \(A = \begin{pmatrix} 3 & 0 \\ 4 & 5 \end{pmatrix}\), vemos que es una aproximación burda. El error en norma de Frobenius sería \(\sqrt{\sigma_2^2} = \sigma_2 = 2.236\).

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Relación con PCA

El Análisis de Componentes Principales (PCA) está íntimamente relacionado con la SVD. Dada una matriz de datos \(X\) de tamaño \(n \times d\) (filas: muestras, columnas: características), centramos los datos restando la media de cada columna, obteniendo \(\tilde{X}\). Entonces la SVD de \(\tilde{X}\) es:
\[
\tilde{X} = U \Sigma V^T
\]
Las columnas de \(V\) son los autovectores de la matriz de covarianza \(\tilde{X}^T \tilde{X}\) (que es proporcional a la matriz de covarianza). Las componentes principales (las proyecciones de los datos sobre las direcciones principales) son \( \tilde{X} V = U \Sigma \). Es decir, las coordenadas de los datos en el nuevo espacio son las columnas de \(U \Sigma\). Los valores singulares están relacionados con la varianza explicada: la varianza a lo largo de la componente \(i\) es \(\sigma_i^2 / (n-1)\).

**Ventaja de usar SVD:** Es numéricamente más estable que calcular la matriz de covarianza y luego sus autovalores, especialmente cuando \(d\) es grande o la matriz está mal condicionada.

##### 2. Sistemas de recomendación (SVD, factorización)

En sistemas de recomendación, tenemos una matriz \(R\) de usuarios × ítems, donde \(R_{ui}\) es la calificación que el usuario \(u\) da al ítem \(i\). Esta matriz es típicamente muy dispersa (la mayoría de las entradas son desconocidas). La **factorización matricial** busca aproximar \(R\) como producto de dos matrices de bajo rango:
\[
R \approx P Q^T
\]
donde \(P\) (usuarios × factores) y \(Q\) (ítems × factores) contienen factores latentes. Esto puede resolverse mediante SVD, pero como la matriz tiene valores faltantes, se usa **SVD incompleto** o algoritmos de optimización como el **Funk SVD** (que minimiza el error cuadrático solo sobre las entradas conocidas).

La SVD completa no es aplicable directamente por los valores faltantes, pero una vez que se tiene la factorización, las predicciones se hacen con el producto punto de los vectores de factores del usuario y el ítem.

**Ejemplo:** Supongamos 3 usuarios y 4 películas, con algunas calificaciones. La factorización con \(k=2\) factores busca matrices \(P\) (3×2) y \(Q\) (4×2) tales que \(P Q^T\) se aproxime a las calificaciones conocidas. Luego, para un usuario \(u\) y una película \(i\) no vista, la predicción es \(\hat{r}_{ui} = \mathbf{p}_u \cdot \mathbf{q}_i\).

##### 3. Análisis Semántico Latente (LSA)

En procesamiento de lenguaje natural, el **Análisis Semántico Latente** (LSA) usa SVD sobre la matriz de términos-documentos (o términos-contextos) para encontrar relaciones semánticas. La matriz \(A\) de tamaño \(t \times d\) (términos × documentos) contiene, por ejemplo, frecuencias de términos. Al aplicar SVD y truncar a rango \(k\), se obtiene una representación de los términos y documentos en un espacio semántico de \(k\) dimensiones, donde términos con significado similar tienen representaciones cercanas. Esto permite buscar documentos por tema y no solo por palabras exactas.

**Procedimiento:**
- Construir matriz \(A\) (términos × documentos) con pesos tf-idf.
- Calcular SVD: \(A = U \Sigma V^T\).
- Reducir a rango \(k\): \(A_k = U_k \Sigma_k V_k^T\).
- Los vectores fila de \(U_k \Sigma_k\) son las representaciones de los términos en el espacio latente.
- Los vectores fila de \(V_k\) (o \(V_k \Sigma_k\)) son las representaciones de los documentos.

#### Deep Learning (DL)

##### 1. LoRA (Low-Rank Adaptation)

LoRA es una técnica de fine-tuning eficiente para modelos grandes. En lugar de actualizar todos los pesos de una capa (matriz \(W_0 \in \mathbb{R}^{d \times k}\)), LoRA inyecta dos matrices de bajo rango \(B \in \mathbb{R}^{d \times r}\) y \(A \in \mathbb{R}^{r \times k}\) (con \(r \ll \min(d,k)\)) y entrena solo \(B\) y \(A\), mientras que \(W_0\) se congela. La nueva matriz de pesos es:
\[
W = W_0 + BA
\]
Esto es una **actualización de bajo rango**. La idea es que los cambios necesarios para adaptarse a una nueva tarea tienen un rango efectivo bajo. Esto reduce drásticamente el número de parámetros entrenables. La SVD está implícita aquí, ya que \(BA\) es una matriz de rango ≤ \(r\), y se puede ver como una aproximación de la actualización completa.

**Ejemplo:** En un transformer, la matriz de proyección de consultas (query) de tamaño 768×768 puede adaptarse con \(r=8\), reduciendo los parámetros entrenables de 590k a solo 12k.

##### 2. Compresión de modelos

La SVD se usa para comprimir modelos grandes, especialmente capas lineales y de embedding. La idea es reemplazar una matriz de pesos \(W\) (de tamaño \(m \times n\)) por su aproximación de bajo rango \(W_k\) obtenida de la SVD. Esto reduce el número de parámetros de \(m \times n\) a \(k(m + n)\). La pérdida de precisión suele ser pequeña si se elige un \(k\) adecuado.

**Ejemplo:** Una capa con \(m=1000\), \(n=1000\) tiene 1M parámetros. Con \(k=100\), la aproximación requiere \(100 \times (1000+1000) = 200k\) parámetros, una reducción del 80%.

##### 3. Compresión de imágenes y datos

La SVD también se aplica directamente a la compresión de imágenes. Una imagen en escala de grises es una matriz de píxeles. Al aplicar SVD y mantener solo los mayores valores singulares, se obtiene una aproximación de bajo rango que ocupa menos espacio. Por ejemplo, para una imagen de 1024×1024, guardar solo los primeros 50 valores singulares y sus vectores requiere \(50 \times (1024+1024) = 102400\) números, en lugar de 1M, una compresión de 10:1.

**Ejemplo paso a paso con una imagen pequeña:**  
Supongamos una imagen de 4×4:
\[
A = \begin{pmatrix}
1 & 2 & 3 & 4 \\
5 & 6 & 7 & 8 \\
9 & 10 & 11 & 12 \\
13 & 14 & 15 & 16
\end{pmatrix}
\]
Su SVD tendrá 4 valores singulares. Si truncamos a \(k=2\), la imagen reconstruida será una aproximación que captura las principales direcciones de variación (básicamente un gradiente lineal). El error será la suma de los cuadrados de los valores singulares descartados.

##### 4. Análisis Semántico Latente (LSA) en NLP

Como mencionamos, LSA es una aplicación clásica de SVD en NLP. Aunque ha sido superada por modelos neuronales, sigue siendo útil para entender la idea de espacios semánticos y como baseline.

##### 5. Sistema de recomendación con factorización matricial

Además de la factorización básica, técnicas como **SVD++** incorporan información implícita. La SVD es la base matemática de estos métodos.

---

