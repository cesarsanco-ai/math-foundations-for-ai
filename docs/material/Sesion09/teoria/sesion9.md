## Semana 9: Tensores

### Teoría

#### 1. Definición de tensor, orden (rank), forma (shape)

Un **tensor** es una generalización de los conceptos de escalar, vector y matriz a un número arbitrario de dimensiones. Es una estructura de datos multidimensional que contiene elementos (generalmente números reales) organizados en una cuadrícula regular.

- **Orden (rank):** Número de dimensiones (ejes) del tensor.
- **Forma (shape):** Tupla que especifica el tamaño de cada dimensión.

| Objeto | Orden (rank) | Forma (shape) | Ejemplo |
|--------|--------------|---------------|---------|
| Escalar | 0 | () | 5 |
| Vector | 1 | (n,) | [1, 2, 3] |
| Matriz | 2 | (m, n) | [[1,2], [3,4]] |
| Tensor 3D | 3 | (d1, d2, d3) | Imagen en escala de grises: (alto, ancho, 1) |
| Tensor 4D | 4 | (d1, d2, d3, d4) | Lote de imágenes color: (batch, alto, ancho, canales) |

**Notación:** Usaremos negrita para tensores de orden ≥ 1. Por ejemplo, \(\mathcal{T}\) para un tensor de orden 3.

**Ejemplo 1:** Un tensor de orden 3 con forma (2, 3, 4) tiene 2 × 3 × 4 = 24 elementos. Podemos visualizarlo como 2 matrices de 3×4 apiladas.

**Ejemplo 2:** En Python con NumPy o PyTorch:
```python
import numpy as np
escalar = np.array(5)
vector = np.array([1, 2, 3])
matriz = np.array([[1,2], [3,4]])
tensor_3d = np.zeros((2,3,4))  # tensor de ceros de forma (2,3,4)
print(tensor_3d.shape)  # (2, 3, 4)
```

#### 2. Representación de datos multidimensionales

Los tensores son la forma natural de representar datos en IA, ya que la mayoría de los datos tienen estructura multidimensional.

##### Imágenes (alto, ancho, canales)
- **Imagen en escala de grises:** Tensor 2D (alto, ancho) o 3D (alto, ancho, 1).
- **Imagen a color (RGB):** Tensor 3D (alto, ancho, canales=3). Cada canal representa la intensidad de rojo, verde y azul.
- **Lote de imágenes:** Tensor 4D (batch_size, alto, ancho, canales). En PyTorch se usa (batch, canales, alto, ancho) por convención.

**Ejemplo:** Una imagen RGB de 224×224 píxeles se representa como un tensor de forma (224, 224, 3). Un lote de 32 imágenes: (32, 224, 224, 3).

##### Secuencias (batch, tiempo, features)
- **Series temporales:** Para una serie con T pasos de tiempo y F características por paso: tensor 2D (T, F) o 3D (batch, T, F) si hay múltiples secuencias.
- **Texto:** Una oración de L palabras, cada palabra representada por un embedding de dimensión D: tensor 2D (L, D). Un lote de B oraciones: tensor 3D (B, L, D).

**Ejemplo:** Un lote de 10 frases, cada una con hasta 20 palabras, usando embeddings de 300 dimensiones: tensor de forma (10, 20, 300). Las frases más cortas se rellenan (padding) con ceros.

##### Lotes (batch)
La dimensión de lote (batch) agrupa múltiples muestras independientes para procesamiento paralelo. Es común en todos los modelos de deep learning.

#### 3. Operaciones tensoriales

##### Suma elemento a elemento
Dos tensores de la misma forma se suman componente a componente.

**Ejemplo:** \(\mathcal{A} = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}\), \(\mathcal{B} = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix}\)  
\(\mathcal{A} + \mathcal{B} = \begin{pmatrix} 6 & 8 \\ 10 & 12 \end{pmatrix}\)

##### Multiplicación elemento a elemento (Hadamard)
También llamada producto de Hadamard: \((\mathcal{A} \odot \mathcal{B})_{ijk} = a_{ijk} b_{ijk}\).

**Ejemplo:** \(\begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} \odot \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix} = \begin{pmatrix} 5 & 12 \\ 21 & 32 \end{pmatrix}\)

##### Producto tensorial (contracciones)
Generaliza el producto de matrices a tensores de orden superior. La operación más común es el **producto punto** (suma sobre un eje común). Por ejemplo, el producto matriz-vector: \(\mathbf{c} = A \mathbf{v}\) equivale a \(c_i = \sum_j A_{ij} v_j\).

Para tensores de orden 3, podemos tener contracciones como \(\mathcal{C}_{ik} = \sum_j \mathcal{A}_{ijk} \mathcal{B}_{jl}\) (sumando sobre j).

#### 4. Broadcasting

El **broadcasting** es una técnica que permite realizar operaciones entre tensores de diferentes formas, "expandiendo" automáticamente las dimensiones más pequeñas para que coincidan con las más grandes. Las reglas:

1. Las dimensiones se comparan desde la última hacia la primera.
2. Dos dimensiones son compatibles si son iguales o una de ellas es 1 (o no existe).
3. Si una dimensión falta en un tensor, se trata como 1.

**Ejemplos paso a paso:**

- Tensor A de forma (3,1) y B de forma (1,4):  
  A se expande a (3,4) repitiendo la columna, B se expande a (3,4) repitiendo la fila. El resultado tiene forma (3,4).

- Tensor A de forma (3,) y B de forma (2,3):  
  A se trata como (1,3) y se expande a (2,3). Resultado (2,3).

- Tensor A de forma (2,3) y B escalar ():  
  B se expande a (2,3). Resultado (2,3).

**Ejemplo numérico:**  
A = [[1, 2, 3], [4, 5, 6]]  (2×3)  
B = [10, 20, 30]  (3,)  
Broadcasting: B se expande a [[10,20,30], [10,20,30]]  
A + B = [[11,22,33], [14,25,36]]

#### 5. Reorganización de dimensiones

##### Reshape
Cambia la forma de un tensor sin alterar el orden de los datos ni el número total de elementos.

**Ejemplo:** Un tensor de forma (2,3,4) con 24 elementos puede reconfigurarse a (6,4), (4,3,2), (2,12), etc., siempre que el producto de las dimensiones sea 24.

```python
import torch
x = torch.randn(2, 3, 4)
y = x.reshape(6, 4)   # ahora y tiene 6 filas y 4 columnas
```

##### Transpose (trasponer)
Intercambia dos dimensiones específicas. Para matrices, es la operación habitual.

**Ejemplo:** \(A\) de forma (3,4) → \(A^T\) de forma (4,3).

##### Permute
Reordena todas las dimensiones según un nuevo orden.

**Ejemplo:** Un tensor de forma (batch, canales, alto, ancho) en PyTorch puede reordenarse a (batch, alto, ancho, canales) con `permute(0, 2, 3, 1)`.

##### Squeeze y Unsqueeze
- **Squeeze:** Elimina dimensiones de tamaño 1.
- **Unsqueeze:** Añade una dimensión de tamaño 1 en una posición específica.

**Ejemplo:**  
`x = torch.randn(1, 3, 1, 4)`  
`x.squeeze()` → forma (3, 4) (elimina dimensiones con tamaño 1)  
`x.unsqueeze(0)` → forma (1, 1, 3, 1, 4) (añade una dimensión al inicio)

#### 6. Producto punto generalizado (einsum)

La notación **einsum** (de Einstein summation) permite expresar operaciones tensoriales complejas de manera concisa. Se basa en la convención de suma de Einstein: índices repetidos en una expresión se suman.

**Sintaxis:** `einsum(índices, tensor1, tensor2, ...)`

**Ejemplos:**

- Producto matriz-matriz: `"ij,jk->ik"`  
  \(C_{ik} = \sum_j A_{ij} B_{jk}\)

- Traza de una matriz: `"ii->"`  
  \(\text{traza}(A) = \sum_i A_{ii}\)

- Producto punto de dos vectores: `"i,i->"`  
  \( \mathbf{a} \cdot \mathbf{b} = \sum_i a_i b_i\)

- Multiplicación elemento a elemento: `"ij,ij->ij"`

- Contracción de tensores de orden 3: `"ijk,ilm->jklm"` (suma sobre i)

**Ejemplo numérico con NumPy:**
```python
import numpy as np
A = np.array([[1,2], [3,4]])
B = np.array([[5,6], [7,8]])
C = np.einsum('ij,jk->ik', A, B)  # producto matricial
print(C)  # [[19,22], [43,50]]
```

#### 7. Tensores en frameworks: PyTorch, TensorFlow

Los frameworks modernos de deep learning están construidos alrededor de tensores y operaciones diferenciables.

- **PyTorch:** Usa `torch.Tensor` como estructura principal. Soporta GPU, autograd (diferenciación automática) y todas las operaciones descritas.
- **TensorFlow:** Usa `tf.Tensor`. Similar, con `tf.GradientTape` para autograd.
- **JAX:** Ofrece tensores con diferenciación automática y compilación JIT.

**Ejemplo en PyTorch:**
```python
import torch
x = torch.randn(32, 3, 224, 224)  # lote de 32 imágenes RGB
w = torch.randn(64, 3, 3, 3)      # 64 kernels de 3×3 con 3 canales de entrada
y = torch.nn.functional.conv2d(x, w)  # convolución
```

#### 8. Aplicaciones en arquitecturas de deep learning

##### CNNs (tensores 4D: batch, canales, alto, ancho)
En PyTorch, la convención es (batch, canales, alto, ancho). En TensorFlow, a veces es (batch, alto, ancho, canales). La operación de convolución aplica kernels (filtros) que son tensores 4D: (canales_salida, canales_entrada, alto_kernel, ancho_kernel).

##### RNNs (tensores 3D: batch, tiempo, features)
Una RNN procesa secuencias. La entrada típica es (batch, seq_len, input_size). La salida puede ser (batch, seq_len, hidden_size) o solo el último estado.

##### Transformers (tensores 3D: batch, secuencia, embedding)
En transformers, la entrada es un tensor de forma (batch, seq_len, d_model). Las matrices de consultas (Q), claves (K) y valores (V) se obtienen multiplicando por matrices de pesos, y la atención se calcula con productos punto entre Q y K.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Reducción de dimensionalidad con SVD o PCA

Aunque SVD y PCA se aplican a matrices, cuando tenemos datos multidimensionales a menudo los convertimos en matrices. Por ejemplo, un dataset de imágenes puede aplanarse: cada imagen de (alto, ancho, canales) se convierte en un vector, formando una matriz de (n_muestras, alto×ancho×canales). Luego se aplica SVD para reducir dimensionalidad.

**Ejemplo con imágenes:** 1000 imágenes de 64×64×3 → matriz de 1000 × (64×64×3) = 1000 × 12288. SVD produce componentes principales que son vectores de longitud 12288, que pueden reconfigurarse a forma (64,64,3) para visualizar los "eigen-images".

##### 2. One-hot encoding

La codificación one-hot convierte variables categóricas en vectores binarios. Por ejemplo, si tenemos 10 categorías, cada categoría se representa como un vector de 10 elementos con un 1 en la posición correspondiente. Esto produce una matriz o tensor.

**Ejemplo:** Un lote de 5 palabras de un vocabulario de 1000 palabras produce un tensor one-hot de forma (5, 1000). En procesamiento de lenguaje, esto se usa antes de las capas de embedding.

#### Deep Learning (DL)

##### 1. CNN: Representación de imágenes y operación de convolución

En una CNN, las imágenes se representan como tensores 4D: (batch, canales, altura, ancho). Los kernels (filtros) son también tensores 4D: (filtros, canales_entrada, altura_kernel, ancho_kernel). La convolución 2D realiza una suma ponderada local:

\[
\text{output}[b, f, i, j] = \sum_{c=0}^{C-1} \sum_{u=0}^{H-1} \sum_{v=0}^{W-1} \text{input}[b, c, i+u, j+v] \cdot \text{weight}[f, c, u, v] + \text{bias}[f]
\]

Esta operación es una contracción tensorial (suma sobre canales de entrada y dimensiones espaciales del kernel).

**Ejemplo:** Entrada: (32, 3, 224, 224) (lote de 32 imágenes RGB 224×224)  
Convolución con 64 kernels de 3×3: peso (64, 3, 3, 3)  
Salida: (32, 64, 222, 222) (sin padding) o (32, 64, 224, 224) con padding.

##### 2. Embeddings: Conversión de palabras en vectores densos

Una capa de embedding es esencialmente una matriz de lookup: para cada índice de palabra, devuelve un vector denso. La entrada es un tensor de índices (por ejemplo, (batch, seq_len)) y la salida es un tensor (batch, seq_len, embedding_dim). Esto se implementa como una multiplicación de la matriz de embedding por los one-hot vectors (eficientemente mediante indexing).

**Ejemplo:** Vocabulario de 10,000 palabras, embedding de 300 dimensiones. Una frase de 20 palabras produce un tensor de entrada de índices (1, 20). La capa de embedding produce un tensor (1, 20, 300).

##### 3. RNN: Modelado de secuencias

En una RNN, la entrada es un tensor 3D: (batch, seq_len, input_size). El estado oculto es un tensor 2D: (batch, hidden_size) (o 3D si se devuelven todos los estados). La operación recurrente es:

\[
h_t = \tanh(W_{ih} x_t + b_{ih} + W_{hh} h_{t-1} + b_{hh})
\]

Esto se aplica a cada paso de tiempo, procesando el tensor a lo largo de la dimensión de secuencia.

**Ejemplo:** Series temporales de 100 pasos con 5 características, lote de 64: entrada (64, 100, 5). Una RNN con hidden_size=128 produce salida (64, 100, 128) si se devuelven todas las secuencias, o (64, 128) si solo el último estado.

##### 4. Transformers: Atención entre tensores Q, K, V

En un transformer, la atención escalada por producto punto se calcula como:

\[
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
\]

Donde Q, K, V son tensores de forma (batch, seq_len, d_k). El producto \(QK^T\) tiene forma (batch, seq_len, seq_len) y luego se multiplica por V para obtener (batch, seq_len, d_v). Todo esto son operaciones tensoriales.

**Ejemplo:** Entrada de 32 frases, cada una de hasta 50 palabras, embedding de 512 dimensiones: Q, K, V son (32, 50, 512). La atención produce (32, 50, 512).

##### 5. Vision Transformers (ViT): Parcheo de imágenes

En ViT, una imagen se divide en parches (patches) de tamaño fijo. Cada parche se aplana y se proyecta linealmente a un embedding. Esto convierte una imagen de (H, W, C) en una secuencia de parches de forma (num_patches, patch_embed_dim). Luego se añade posición y se procesa con un transformer.

**Ejemplo:** Imagen 224×224 RGB, parches de 16×16: número de parches = (224/16)² = 196. Cada parche se aplana a 16×16×3 = 768. Tras proyección lineal, se obtiene un tensor (196, embed_dim). Con lote de 32 imágenes: (32, 196, embed_dim).

##### 6. Series Temporales con RNNs/LSTMs

Los datos de series temporales multivariadas se representan como tensores 3D: (batch, timesteps, features). Por ejemplo, datos de sensores con 10 mediciones cada 5 minutos durante 24 horas (288 pasos), lote de 100: (100, 288, 10).

##### 7. Transfer Learning: Congelación de "rebanadas" de tensores

En transfer learning, se cargan pesos pre-entrenados (tensores) y se "congelan" ciertas capas, es decir, se evita que se actualicen durante el entrenamiento. Esto se hace configurando `requires_grad=False` en PyTorch. Las "rebanadas" (slicing) de tensores pueden seleccionarse para fine-tuning parcial.

**Ejemplo:** Cargar ResNet pre-entrenada y congelar todas las capas excepto la última (clasificador). Los pesos de las capas convolucionales son tensores 4D que permanecen fijos; solo se entrena el tensor de la última capa lineal.

##### 8. Broadcasting en operaciones

Broadcasting es esencial para eficiencia. Por ejemplo, al normalizar un lote de imágenes, se resta la media por canal (un tensor de forma (3,)) a cada imagen (H,W,3). Broadcasting expande automáticamente la media a (H,W,3).

**Ejemplo:** Normalización por lotes (BatchNorm): durante entrenamiento, se mantiene una media móvil por canal (tensor (C,)). Al aplicarla a un tensor (N,C,H,W), broadcasting permite restar la media a todos los píxeles de cada canal sin bucles explícitos.

##### 9. Reorganización de dimensiones (reshape, transpose, permute)

Estas operaciones son cruciales para conectar capas. Por ejemplo, antes de una capa lineal en una CNN, se suele aplanar el tensor: de (batch, C, H, W) a (batch, C*H*W) con `reshape`. En transformers, a veces se permutan dimensiones para compatibilidad entre diferentes frameworks.

**Ejemplo:** En una CNN para clasificación, tras las capas convolucionales, tenemos (batch, 512, 7, 7). Se aplica `reshape(batch, 512*7*7)` para conectar con una capa lineal de salida.

##### 10. Autoencoders y modelos generativos

Los autoencoders comprimen datos a una representación latente (codificación) y luego reconstruyen. Los tensores fluyen a través del codificador (que reduce dimensiones) y el decodificador (que las expande). En modelos generativos como VAE o GANs, los tensores se manipujan continuamente con operaciones de reshaping, convoluciones transpuestas, etc.

**Ejemplo:** Un autoencoder convolucional para imágenes: entrada (batch, 3, 64, 64) → codificador produce (batch, 128, 8, 8) → aplanado a (batch, 128*8*8) → capa densa a (batch, latent_dim) → decodificador: capa densa a (batch, 128*8*8) → reshape a (batch, 128, 8, 8) → convoluciones transpuestas hasta (batch, 3, 64, 64).

---

