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
(La pérdida define qué significa equivocarse, El optimizador define cómo corregir el error)
- Ejemplos de problemas: regresión, clasificación, clustering, generación.
- Motivación de las herramientas matemáticas: ¿por qué necesitamos álgebra lineal, cálculo y probabilidad?
- Panorama del curso: cómo cada bloque matemático sustentará los modelos futuros.

### Aplicaciones prácticas
- Ideas matematicas de funciones de perdida (distancia, probabilidad, margen geometrico): distancias (MSE, MAE, K-means); log-likelihood, probabilidad (Cross Entropy, Log Loss); margen geométrico (Hinge Loss, SVM)
- optimizacion: min ​L(θ1,θ2,θ3,..)
- (Flujo tipico: Definir Modelo + prediccion + funcion de perdida + algoritmo de optimizacion + actualizacion de parametros/ Casos en regresion, logistica, RRNN, K-means, decision tree)
- Formas de optimizacion: formulas analiticas (ML clasico), gradiente (DL)
- Algoritmos para calcular gradientes (SGD, adam, RMSProp, etc)
- Diferencias de optimizacion en ML y DL: conceptos de backpropagation en Regresion, Clasificacion
    * Tipo de problema vs ¿que mide la perdida? (
        | Tipo problema | Qué mide la pérdida             |
| ------------- | ------------------------------- |
| Regresión     | distancia entre números         |
| Clasificación | diferencia entre probabilidades |
| Clustering    | compactación de clusters        |
| Deep Learning | cualquiera de las anteriores    |
| Reinforcement | error de estimación de valor    |

    * metodos de optimizacion:
    | Método                            | Dónde se usa     | Formula
    | --------------------------------- | ---------------- |
    | Gradient Descent                  | ML clásico y DL  |
    | Stochastic Gradient Descent (SGD) | datasets grandes |
    | Adam                              | Deep Learning    |
    | Closed-form solution              | regresión lineal |
    | EM Algorithm                      | clustering       |
- Interpretaciones
| Término            | Significado exacto                                           |
| ------------------ | ------------------------------------------------------------ |
| Loss function      | error **por ejemplo individual**                             |
| Cost function      | promedio o suma del error en el **dataset**                  |
| Objective function | función total que se optimiza (puede incluir regularización) |

# 1. Forma general del problema en ML

Casi todos los modelos se formulan como:

[
\min_{\theta} L(\theta)
]

donde:

* (L) = función de pérdida
* (\theta) = parámetros del modelo

Pero en realidad casi siempre es:

[
L(\theta) = \frac{1}{n}\sum l(y_i,\hat y_i)
]

donde:

* (l) = loss individual
* (L) = costo total

---

# 2. Regresión

Modelo típico:

[
\hat y = f(x;\theta)
]

Parámetros:

[
\theta = (w,b)
]

Loss más común:

MSE

MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2

### Parámetros optimizados

[
\theta = (w_1, w_2, ..., w_p, b)
]

### Optimizadores usados

| método           | uso              |
| ---------------- | ---------------- |
| Closed form      | regresión lineal |
| Gradient Descent | datasets grandes |
| SGD              | online learning  |

---

# 3. Clasificación

Modelo típico:

[
p(y|x;\theta)
]

Loss más usada: **cross entropy**

[
L = -\sum y_i \log(p_i)
]

### Parámetros

[
\theta = (w,b)
]

pero el modelo produce probabilidades.

---

### Optimización

| algoritmo        | modelo              |
| ---------------- | ------------------- |
| Gradient Descent | logistic regression |
| LBFGS            | logistic regression |
| SGD              | modelos grandes     |

---

# 4. Clustering

Aquí cambia el paradigma.

No hay (y).

Modelo:

[
cluster(x)
]

Loss típica: **SSE**

[
L = \sum ||x_i - \mu_k||^2
]

### Parámetros optimizados

[
\theta = {\mu_1,\mu_2,...,\mu_k}
]

los centroides.

### Optimización

| algoritmo                |
| ------------------------ |
| K-means iterative update |
| EM algorithm             |

No usan gradiente normalmente.

---

# 5. Árboles de decisión

Loss:

* Gini
* Entropy

Ejemplo:

[
Entropy = -\sum p_i \log p_i
]

### Parámetros

no son continuos.

Son:

* variables de split
* thresholds

### Optimización

algoritmo **greedy**.

---

# 6. Deep Learning

Modelo:

[
\hat y = f(x;\theta)
]

pero

[
\theta = millones\ de\ pesos
]

Loss depende de la tarea:

| tarea         | loss          |
| ------------- | ------------- |
| regresión     | MSE           |
| clasificación | cross entropy |
| detección     | focal loss    |

### Optimización

| optimizador |
| ----------- |
| SGD         |
| Adam        |
| RMSprop     |

con **backpropagation**.

---

# 7. Regularización (parte del objective)

Muchas veces la función final es:

[
L(\theta) = Loss + \lambda R(\theta)
]

Ejemplo:

L2 regularization

[
L = MSE + \lambda ||\theta||^2
]

Esto controla **overfitting**.

---

# 8. ¿Todos dependen de un solo parámetro?

No.

En general:

[
\theta \in \mathbb{R}^d
]

puede haber:

* decenas
* miles
* millones

Ejemplo:

| modelo           | # parámetros |
| ---------------- | ------------ |
| regresión lineal | pocos        |
| random forest    | miles        |
| deep learning    | millones     |

---

# 9. Resumen conceptual

Todos los modelos ML siguen esta estructura:

| Paso | concepto              |
| ---- | --------------------- |
| 1    | modelo (f(x;\theta))  |
| 2    | pérdida (L(y,\hat y)) |
| 3    | objetivo (L(\theta))  |
| 4    | optimización          |

---

# 10. Los optimizadores más usados en la práctica

### ML clásico

| optimizador        |
| ------------------ |
| closed form        |
| gradient descent   |
| coordinate descent |
| EM                 |

---

### Deep learning

| optimizador |
| ----------- |
| SGD         |
| Adam        |
| AdamW       |
| RMSprop     |

Adam domina actualmente.

---

# 11. Insight importante (muy útil)

Casi **todo ML moderno** se puede escribir así:

[
\min_\theta \frac{1}{n}\sum l(y_i,f(x_i;\theta))
]

esto se llama:

**Empirical Risk Minimization (ERM)**.

---

💡 **Idea clave**

Toda rama de ML cambia solo estas tres cosas:

| elemento     | qué cambia    |
| ------------ | ------------- |
| modelo       | (f(x;\theta)) |
| loss         | (l(y,\hat y)) |
| optimización | algoritmo     |

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

