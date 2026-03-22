# Sílabo del Curso: Cálculo y Álgebra Lineal para Inteligencia Artificial

**Duración:** 14 semanas  
**Objetivo:** Proporcionar los fundamentos matemáticos necesarios para comprender y desarrollar modelos de Machine Learning y Deep Learning. Cada semana combina teoría matemática con aplicaciones prácticas que se encontrarán en cursos posteriores de ML y DL, mostrando la conexión directa entre los conceptos y su uso en IA.

---

## Semana 1: Fundamentos Matemáticos

### Teoría
- Notación matemática: índices, sucesiones, series, sumatorias y productorias simples, dobles y triples.
- Sistemas de dimensiones: 2D, 3D, n-dimensional
- Estructura de datos: Grafos 
- Objetos matematicos: Escalares, vectores, matrices, tensores
- Funciones elementales: lineales, polinomiales, exponenciales, logarítmicas, trigonometricas, trigonometricas hiperbolicas
- Tipos de funciones por dominio: composicion de funciones, funciones por tramos
- Funciones de activación: sigmoide, tanh, ReLU.
- Concepto de función de pérdida: definición general y ejemplos intuitivos (distancia entre números, diferencia entre probabilidades).

### Aplicaciones prácticas
- **ML:** Regresión lineal (función lineal), regresión logística (sigmoide, softmax), SVM (kernel RBF: exponencial), entropía (logaritmo), funciones de pérdida (log-loss).  
- **DL:** Perceptrón (función lineal + activación), funciones de activación (ReLU, GELU), positional encoding (seno/coseno), RNN (tanh, sigmoide), atención (softmax).

---

## Semana 2: Fundamentos de IA

### Teoría
- ¿Qué es la Inteligencia Artificial? Definiciones y alcance.
- Tipos de aprendizaje: supervisado, no supervisado, por refuerzo (con ejemplos).
- Estructura general de un modelo de IA: función de predicción \(f(x;\theta)\), función de pérdida \(L(\theta)\), optimización.
  - La pérdida define qué significa equivocarse.
  - El optimizador define cómo corregir el error.
- Ejemplos de problemas: regresión, clasificación, clustering, generación.
- Motivación de las herramientas matemáticas: ¿por qué necesitamos álgebra lineal, cálculo y probabilidad?
- Panorama del curso: cómo cada bloque matemático sustentará los modelos futuros.
- Forma general del problema en ML: \(\min_{\theta} L(\theta) = \frac{1}{n}\sum l(y_i,\hat y_i)\) (Empirical Risk Minimization).
- Diferencias entre loss function, cost function y objective function.
- Regularización como parte del objective: \(L(\theta) = Loss + \lambda R(\theta)\).

### Aplicaciones prácticas
- **ML:** 
  - Ideas matemáticas de funciones de pérdida según tipo de problema:
    - **Regresión:** distancia entre números (MSE, MAE)
    - **Clasificación:** diferencia entre probabilidades (Cross Entropy, Log Loss)
    - **Clustering:** compactación de clusters (SSE, K-means)
    - **SVM:** margen geométrico (Hinge Loss)
  - Flujo típico: Definir Modelo + predicción + función de pérdida + algoritmo de optimización + actualización de parámetros.
  - Casos concretos: regresión lineal, regresión logística, K-means, árboles de decisión.
  - Optimización: closed-form (regresión lineal), gradient descent, SGD, Adam, EM Algorithm.
  - Optimizadores en la práctica: closed form, gradient descent, coordinate descent, EM (ML clásico); SGD, Adam, AdamW, RMSProp (DL).
- **DL:** 
  - Backpropagation como aplicación de la regla de la cadena multivariable.
  - Diferencias de optimización en ML y DL según el tipo de problema y el número de parámetros.
  - Parámetros en diferentes modelos: regresión lineal (pocos), random forest (miles), deep learning (millones).


---

## Semana 3: Matrices

### Teoría
- Definición de matriz, tipos (cuadrada, diagonal, identidad, triangular).
- Vectores como matrices de una columna: definición, suma, resta, multiplicación por escalar.
- Operaciones: suma de matrices, producto de matrices, multiplicación matriz–vector, transposición.
- Propiedades: determinante, inversa, rango.
- Representación de datasets como matrices (filas = muestras, columnas = features).

### Aplicaciones prácticas
- **ML:** Matriz de covarianza, Regresión lineal (representación matricial, solución normal), regresión logística (matriz de features), PCA (matriz de covarianza), factorización matricial en sistemas de recomendación.  
- **DL:** Pesos como matrices en capas lineales, backpropagation (operaciones matriciales), inicialización de pesos (varianza), convoluciones (operaciones matriciales), Transformers (multiplicación de matrices en atención).

---

## Semana 4: Sistemas de Ecuaciones Lineales

### Teoría
- Sistemas lineales: representación \(Ax = b\).
- Interpretación geométrica (intersección de rectas/planos).
- Eliminación gaussiana.
- Tipos de solución: única, infinitas, inconsistente.
- Sistemas sobredeterminados y solución por mínimos cuadrados.

### Aplicaciones prácticas
- **ML:** Regresión lineal (mínimos cuadrados).  
- **DL:** (Base conceptual para optimización, subyace en problemas de ajuste).

---

## Semana 5: Espacios Vectoriales y Normas

### Teoría
- Espacio vectorial ℝⁿ, subespacios.
- Combinación lineal, independencia lineal, bases, dimensión, cambio de base.
- Producto punto, ángulo entre vectores, similitud coseno.
- Normas: L1, L2, L∞; interpretación geométrica.
- Distancias: euclidiana, Manhattan, Chebyshev; bola unitaria.
- Proyecciones ortogonales.
- Rectas, planos e hiperplanos; semiespacios.
- Concepto de regularización basada en normas.

### Aplicaciones prácticas
- **ML:** Regularización Ridge (L2) y Lasso (L1), KNN (distancias), SVM (producto punto, margen, normas), clustering (distancias, silhouette), sistemas de recomendación (similitud coseno), Huber loss.  
- **DL:** Regularización en redes (normas de pesos), LoRA (normas de matrices), atención (producto punto Q·K), RAG (búsqueda de vecinos, distancias), CLIP (similitud coseno).

---

## Semana 6: Transformaciones Lineales

### Teoría
- Definición de transformación lineal.
- Representación matricial.
- Composición de transformaciones.
- Tipos: rotaciones, escalados, proyecciones.
- Interpretación de capas de redes como transformaciones.

### Aplicaciones prácticas
- **ML:** Feature engineering, Regresión lineal (transformación lineal), SVM con kernel (mapeo a espacio de características).  
- **DL:** Capas lineales, redes profundas como composición de transformaciones, kernel en CNN, compresión y representación de audio, imágenes, video y datos

---

## Semana 7: Autovalores y Autovectores

### Teoría
- Definición de autovalor y autovector.
- Ecuación característica.
- Interpretación geométrica: direcciones invariantes.
- Diagonalización de matrices.
- Descomposición espectral.

### Aplicaciones prácticas
- **ML:** PCA (autovalores de la matriz de covarianza).  
- **DL:** (Concepto subyacente en análisis de representaciones, ej. en estabilidad de dinámicas).

---

## Semana 8: Descomposición de Matrices 

### Teoría
- Descomposición en valores singulares (SVD): \(A = U\Sigma V^T\).
- Interpretación geométrica.
- Pseudoinversa de Moore–Penrose.
- Aproximaciones de bajo rango.

### Aplicaciones prácticas
- **ML:** PCA (relacionado), sistemas de recomendación (SVD, factorización).  
- **DL:** LoRA (descomposición de bajo rango), compresión de modelos, compresion de imagenes y datos, analisis semantico latente (LSA), sistema de recomendacion

---

## Semana 9: Tensores

### Teoría
- Definición de tensor, orden (rank), forma (shape).
- Representación de datos multidimensionales: imágenes (alto, ancho, canales), secuencias (batch, tiempo, features), lotes (batch).
- Operaciones tensoriales: suma, multiplicación elemento a elemento, producto tensorial (contracciones).
- Broadcasting: reglas para operar tensores de diferentes formas.
- Reorganización: reshape, transpose, permute, squeeze, unsqueeze.
- Producto punto generalizado (einsum).
- Tensores en frameworks: PyTorch, TensorFlow (mención).
- Aplicaciones: representación de datos en CNNs (tensores 4D: batch, canales, alto, ancho), RNNs (tensores 3D: batch, tiempo, features), Transformers (tensores 3D: batch, secuencia, embedding).

### Aplicaciones prácticas
- **ML:** Reduccion de dimensionalidad con SVA o PCA, one-hot encoding
- **DL:** 
CNN (Batch, Canales, Altura, Ancho), Aplicación de Filtros/Kernels: Operación de convolución como un producto de tensores que extrae mapas de características
Embeddings: Conversión de palabras en vectores densos (tensores de rango 1) que se agrupan en secuencias (rango 2) y lotes (rango 3).
RNN
Transformers: puntuacion de atencion entre tensores Q,K,V
Vision Transformers (parcheo de imágenes)
Series Temporales (RNNs/LSTMs): Modelado de datos con dependencia temporal usando tensores 3D: [Batch, Timesteps, Features].
Transfer Learning: Congelación de "rebanadas" (slicing) de tensores de pesos en modelos pre-entrenados para ajustarlos a nuevas tareas.
Broadcasting
Reorganizacion de dimensiones (reshape, transpose, permute)
Autoencoders y modelos generativos
---

## Semana 10: Probabilidad y Estadística para IA

### Teoría
- Probabilidad básica: axiomas, probabilidad condicional, independencia, teorema de Bayes.
- Variables aleatorias, esperanza, varianza, covarianza.
- Distribuciones: normal, Bernoulli, multinomial, uniforme.
- Estadística descriptiva: media, mediana, moda, desviación estándar, cuartiles, correlación (Pearson, Spearman).
- Entropía, información mutua, divergencia KL.
- Tests estadísticos: Kolmogorov–Smirnov, PSI, p-valor, intervalos de confianza.

### Aplicaciones prácticas
- **ML:** EDA (estadística descriptiva), regresión logística (probabilidad), Naive Bayes (teorema de Bayes), árboles (entropía, Gini), bias‑varianza (varianza), PCA (matriz de covarianza), series de tiempo (autocorrelación), RANSAC, Adjusted Rand Index, Shapley (valor esperado), tests A/B (significancia).  
- **DL:** Dropout (Bernoulli), inicialización (varianza), Batch Norm (media, varianza), modelos de lenguaje (probabilidad de secuencias), modelos generativos (distribuciones, divergencia KL), CLIP (softmax, pérdida contrastiva).

---

## Semana 11: Límites y Continuidad

### Teoría
- Concepto de límite (intuitivo y formal básico).
- Continuidad de funciones, tipos de discontinuidades.
- Propiedades de funciones continuas (teorema del valor intermedio).
- Comportamiento local y estabilidad.

### Aplicaciones prácticas
- **ML:** Funciones de pérdida (necesidad de continuidad para optimización), optimización (convergencia).  
- **DL:** Estabilidad de funciones de activación, convergencia de entrenamiento.

---

## Semana 12: Derivadas e Integrales en una variable

### Teoría
- Derivada como tasa de cambio, interpretación geométrica.
- Reglas de derivación (producto, cociente, cadena).
- Derivacion simple y de orden n
- Derivadas de funciones elementales (polinomios, exponencial, logaritmo, seno, coseno, sigmoide, tanh).
- Derivada de funciones compuestas
- Integral definida como área bajo la curva, teorema fundamental del cálculo.
- Aplicación: cálculo de áreas (AUC).

### Aplicaciones prácticas
- **ML:** Derivadas para gradiente en regresión en 1D, derivada de sigmoide y log-loss, gradiente en boosting, AUC (integral), Integrales en probabilidades 
- **DL:** Derivadas en backprop (regla de la cadena), derivadas de funciones de activación, pérdidas basadas en integrales (cross-entropy).

---

## Semana 13: Cálculo Multivariable

### Teoría
- Funciones de varias variables, representación y visualización.
- Derivadas parciales.
- Vector gradiente, interpretación geométrica (dirección de máximo crecimiento).
- Regla de la cadena multivariable.
- Matriz Jacobiana y Hessiana (introducción y significado).

### Aplicaciones prácticas
- **ML:** Gradiente de funciones de costo con múltiples parámetros, gradiente de log-loss, superficie de pérdida.  
- **DL:** Backpropagation (regla de la cadena multivariable), gradiente en redes profundas, gradiente evanescente/explosivo (producto de Jacobianos), optimizadores (Adam, etc.).

---

## Semana 14: Optimización y Gradiente Descendente

### Teoría
- Funcion concava, convexa
- Maximo, minimo local y global
- Problemas de optimización: minimización de funciones.
- Descenso de gradiente: algoritmo, interpretación geométrica.
- Variantes: SGD, Momentum, Adam, RMSprop.
- Programación de learning rate (step decay, cosine annealing).
- Regularización como penalización en la función objetivo (L1, L2).
- Condiciones de optimalidad (puntos críticos, convexidad básica).

### Aplicaciones prácticas
- **ML:** Descenso de gradiente en regresión y clasificación, gradient boosting (optimización), búsqueda de hiperparámetros.  
- **DL:** SGD, Momentum, Adam, AdamW, cosine annealing, optimización en agentes autónomos.

---

