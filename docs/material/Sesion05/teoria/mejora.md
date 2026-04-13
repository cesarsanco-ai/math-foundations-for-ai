

# 📘 Espacios Vectoriales para Ingeniería en IA  
## Temario de estudio (sin código, sin transformaciones lineales)

**Objetivo:** Comprender los espacios vectoriales como el lenguaje geométrico detrás de modelos de Machine Learning, Deep Learning, NLP y GenAI. Cada concepto se conecta directamente con aplicaciones reales: KNN, embeddings, regularización, SVM, kernels, etc.

---

## Módulo 1: Fundamentos de Espacios Vectoriales

### Definición y axiomas
Un espacio vectorial es un conjunto de elementos (vectores) que se pueden sumar entre sí y multiplicar por números reales (escalares), cumpliendo ciertas propiedades (asociatividad, conmutatividad, existencia de vector nulo, etc.).

### Ejemplos relevantes en IA
- **ℝⁿ**: vectores de características (edad, ingreso, compras), embeddings de palabras, pesos de una red.
- **Espacios de funciones**: utilizados en kernels y modelos generativos.
- **Espacios de matrices**: capas lineales de una red.

### ¿Por qué es importante?
Todo dato que alimenta un modelo de IA se representa como un vector. Las operaciones que hacemos (similaridad, clasificación, generación) ocurren dentro de estos espacios.

---

## Módulo 2: Subespacios Vectoriales

### Definición
Un subespacio es un subconjunto de un espacio vectorial que a su vez es un espacio vectorial (cerrado bajo suma y escalado).

### Subespacios clave en IA
- **Espacio generado por los datos (span)**: todas las combinaciones lineales de las muestras. Define lo que el modelo puede representar.
- **Espacio latente**: subespacio de baja dimensión aprendido por autoencoders o modelos generativos (VAE, GAN, difusión).

### Aplicación práctica
- En **GenAI**, el espacio latente es un subespacio donde cada punto genera una imagen, texto o audio nuevo. Interpolar entre dos puntos (combinación convexa) produce transiciones suaves.
- En **reducción de dimensionalidad implícita**, el modelo ignora direcciones no relevantes, trabajando en un subespacio más pequeño.

---

## Módulo 3: Combinaciones Lineales, Span e Independencia Lineal

### Combinación lineal
Expresión de la forma \( c_1 v_1 + c_2 v_2 + \dots + c_k v_k \).

### Span (conjunto generador)
El conjunto de todas las combinaciones lineales posibles de un grupo de vectores.

### Independencia lineal
Un conjunto es linealmente independiente si ningún vector puede escribirse como combinación lineal de los demás.

### Aplicaciones en IA
- **Detección de redundancia**: si dos características son linealmente dependientes (ej. temperatura en °C y °F), una sobra. Se detecta con independencia lineal.
- **Embeddings**: se busca que las dimensiones sean lo más independientes posible para capturar distintos aspectos semánticos.
- **Regularización**: penalizar combinaciones lineales complejas (indirectamente relacionado).

---

## Módulo 4: Bases, Dimensión y Cambio de Base

### Base
Un conjunto de vectores linealmente independientes que genera todo el espacio. Cualquier vector se expresa de forma única como combinación lineal de la base.

### Dimensión
Número de vectores en una base. Es la “cantidad de direcciones independientes” del espacio.

### Cambio de base
Transformación que permite expresar un mismo vector en diferentes sistemas de coordenadas.

### Aplicaciones en IA
- **Embeddings de palabras (Word2Vec, GloVe, BERT)**: cada palabra es un vector en una base aprendida. Al cambiar de base (por ejemplo, proyectar con PCA –tema aparte–) se pueden visualizar relaciones semánticas.
- **Kernels**: el truco del kernel consiste en aplicar un cambio de base implícito a un espacio de mayor dimensión para hacer linealmente separable un problema que originalmente no lo era.
- **Espacio latente en GenAI**: la base del espacio latente determina qué atributos (estilo, contenido, color) son controlables independientemente.

---

## Módulo 5: Espacios con Producto Interno – Geometría para la IA

### Producto escalar (dot product)
Dados dos vectores, \( \langle u, v \rangle = u_1 v_1 + \dots + u_n v_n \). Mide cuánto se alinean.

### Norma (longitud)
- **Norma L2**: \( \|v\|_2 = \sqrt{v_1^2 + \dots + v_n^2} \). Distancia euclidiana.
- **Norma L1**: \( \|v\|_1 = |v_1| + \dots + |v_n| \). Distancia Manhattan.
- **Norma L∞**: \( \|v\|_\infty = \max(|v_1|, \dots, |v_n|) \). Distancia de Chebyshev.

### Bola unitaria
Conjunto de vectores con norma ≤ 1. Su forma cambia según la norma:
- **L2**: esfera (círculo en 2D).
- **L1**: diamante (rombo).
- **L∞**: cuadrado alineado a los ejes.

### Distancias comunes en IA
- **Euclidiana (L2)**: sensible a magnitudes, usada en KNN cuando las características tienen escalas similares.
- **Manhattan (L1)**: más robusta a outliers, útil en datos de alta dimensión.
- **Coseno**: \( \cos(\theta) = \frac{\langle u, v \rangle}{\|u\|_2 \|v\|_2} \). Mide ángulo, no magnitud. Esencial para comparar embeddings (textos, imágenes, recomendaciones).

### Aplicaciones directas

#### 🔹 KNN (K‑vecinos más cercanos)
- Puede usar cualquier distancia: L2, L1, coseno, etc.
- **Elección de la distancia** afecta el rendimiento:
  - Datos continuos y sin outliers → L2.
  - Datos con muchas dimensiones y valores cero → L1 (más robusta).
  - Embeddings normalizados → coseno (ignora longitud del vector).

#### 🔹 Regularización L1 y L2 (weight decay)
- Se añade un término a la función de pérdida: \( \lambda \|w\|_1 \) o \( \lambda \|w\|_2^2 \).
- **Interpretación geométrica**: la solución óptima debe estar dentro de la bola unitaria de la norma correspondiente (L1 o L2). La bola L1 tiene esquinas en los ejes → induce soluciones sparse (muchos pesos cero). La bola L2 es redonda → pesos pequeños pero no exactamente cero.

#### 🔹 SVM lineal
- Busca el hiperplano que maximiza el margen. El margen es inversamente proporcional a la norma L2 del vector normal \( w \).
- Minimizar \( \|w\|_2^2 \) equivale a maximizar el margen.

---

## Módulo 6: Ortogonalidad, Proyecciones y Descomposición Ortogonal

### Ortogonalidad
Dos vectores son ortogonales si su producto interno es cero. Si además tienen norma 1, se llaman ortonormales.

### Proyección ortogonal
Dado un vector \( v \) y un subespacio \( S \), la proyección es el vector en \( S \) más cercano a \( v \) (en distancia L2). Es la “sombra” de \( v \) sobre \( S \).

### Proceso de Gram‑Schmidt
Método para obtener una base ortonormal a partir de cualquier base.

### Aplicaciones en IA

#### 🔹 Regresión lineal
La solución de mínimos cuadrados es la proyección ortogonal del vector de salidas sobre el espacio generado por las características. Por eso se llama “proyección”.

#### 🔹 Kernels y espacios RKHS
En SVM con kernel, los datos se mapean a un espacio de funciones (espacio de Hilbert con núcleo reproductor – RKHS). La ortogonalidad en ese espacio determina la separabilidad de clases.

#### 🔹 Eliminación de ruido
Si el ruido es ortogonal a la señal, proyectar sobre el subespacio de la señal lo elimina. Idea base de filtrado y autoencoders lineales.

---

## Módulo 8: Espacios Vectoriales en Alta Dimensión y Aplicaciones Integradas

### Problemas de alta dimensionalidad (“maldición”)
A medida que aumenta la dimensión \( d \), el volumen del espacio crece exponencialmente. Los datos se vuelven esparcidos y las distancias pierden contraste (todas las distancias tienden a ser similares).

### Consecuencias prácticas
- **KNN en alta dimensión** (ej. imágenes de 1024 píxeles) requiere muchas muestras y puede fallar si no se reduce dimensión.
- **Embeddings** (word2vec, BERT) típicamente usan 300–768 dimensiones: es un equilibrio entre expresividad y maldición.
- **Bases de datos vectoriales** (para búsqueda semántica) usan índices especiales (HNSW, IVF) porque la búsqueda exacta por distancia es muy costosa.

### Aplicaciones integradas (sin código)

#### 🔹 Embeddings vectoriales
- **Word2Vec / GloVe / FastText**: palabras → vectores en ℝᵈ. La similitud coseno captura relaciones semánticas (“rey” – “hombre” + “mujer” ≈ “reina”).
- **Sentence embeddings (SBERT)**: frases completas → vectores. Permiten búsqueda semántica en documentos.
- **Imágenes**: redes CNN extraen embeddings de imágenes para búsqueda por similitud.

#### 🔹 Regularización vía normas (repaso aplicado)
- **L2** → pesos pequeños, ninguna característica domina excesivamente. Mejora generalización.
- **L1** → produce sparse feature selection (algunos pesos exactamente cero). Útil cuando se tienen muchas características irrelevantes.

#### 🔹 SVM con kernels
- El kernel \( K(x, y) = \langle \phi(x), \phi(y) \rangle \) es un producto interno en un espacio de características de alta dimensión (posiblemente infinito).
- Ejemplo: kernel polinomial, RBF (gaussiano). Permite clasificar datos no linealmente separables sin calcular explícitamente \( \phi(x) \).

#### 🔹 Generative AI (espacios latentes)
- En VAE, GAN y difusión, el generador aprende un mapeo desde un espacio latente (generalmente ℝᵈ con d pequeña, ej. 100–512) hacia el espacio de datos (imágenes, texto, audio).
- **Interpolación**: tomar dos puntos latentes y generar la serie de puntos intermedios (combinación convexa) produce transiciones suaves y realistas.
- **Edición de atributos**: mover el vector latente en una dirección específica (ej. “gafas”) modifica el atributo en la salida.

#### 🔹 Bases de datos vectoriales (concepto)
- Almacenan embeddings y permiten búsqueda por similitud (producto interno o distancia L2).
- Motor de búsqueda semántica, recomendación, RAG (Retrieval-Augmented Generation).

---

## Resumen de conexiones (tabla para repaso rápido)

| Concepto matemático | Aplicación en IA |
|---------------------|------------------|
| Espacio vectorial | Representación de datos (features, embeddings, pesos) |
| Subespacio | Espacio latente en autoencoders / GenAI |
| Independencia lineal | Detección de features redundantes |
| Cambio de base | Kernels (mapeo implícito a otro espacio) |
| Norma L1 / L2 / L∞ | Regularización (Lasso, Ridge), bolas unitarias |
| Distancia L1, L2, coseno | KNN, búsqueda de vecinos, similaridad de embeddings |
| Producto interno | Atención (Attention), similitud coseno, SVM lineal |
| Proyección ortogonal | Regresión lineal (mínimos cuadrados), eliminación de ruido |
| Bola unitaria | Región factible para pesos en regularización |
| Alta dimensionalidad | Maldición, embeddings, bases de datos vectoriales |

---

