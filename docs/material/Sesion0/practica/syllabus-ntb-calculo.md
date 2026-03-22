# Curso de Cálculo y Álgebra Lineal para Inteligencia Artificial
## Syllabus de Notebooks por Semana

**Carlos César Sánchez Coronel**

2026

---

## Filosofía del Curso

Cada concepto matemático se presenta en su forma abstracta, pero inmediatamente se muestra su "huella digital" en el mundo de la IA. En cada notebook conceptual (NB1) se incluirá una sección llamada **"Conexiones IA"** donde, con datos dummy, se visualizará la ecuación y se explicará su rol en áreas como Machine Learning, Deep Learning, NLP, Visión por Computador, Sistemas de Recomendación, Robótica y Modelos Generativos.

---

## Estructura General por Semana

- **Notebook Conceptual (NB1):** Experimentación con datos sintéticos, implementación de ecuaciones desde cero, visualización de conceptos y sección "Conexiones IA" con aplicaciones en diversas ramas.
- **Notebook de Ejercicios (NB2):** Aplicación sobre datasets reales (imágenes, textos, datos tabulares) para reforzar y transferir el aprendizaje.

---

## Semana 1: Fundamentos Matemáticos

### Propósito
Establecer las bases matemáticas y de notación que se utilizarán durante todo el curso, conectando desde el primer momento los conceptos abstractos con sus aplicaciones en IA.

### Notebook Conceptual (NB1) – Visualizando el Lenguaje Matemático

- **Datos:** Arrays de NumPy generados con `np.linspace`, `np.arange`, estructuras de datos simuladas.
- **Actividades:**
  1. Representación de escalares, vectores, matrices y tensores como estructuras de datos en Python.
  2. Notación de sumatorias simples, dobles y triples ($\sum$) aplicadas a operaciones en ML.
  3. Visualización de funciones elementales: lineal ($f(x)=mx+b$), polinomial, exponencial ($e^x$), logarítmica ($\ln x$), seno, coseno, tanh.
  4. Visualización de funciones de activación: sigmoide ($\sigma(x)=\frac{1}{1+e^{-x}}$), ReLU ($\max(0,x)$), tanh.
  5. Composición de funciones y funciones por tramos.
  6. Concepto intuitivo de función de pérdida: distancia entre números, diferencia entre probabilidades.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Regresión lineal (función lineal), regresión logística (sigmoide, softmax), SVM (kernel RBF: exponencial), entropía (logaritmo), funciones de pérdida (log-loss).
  - **DL:** Perceptrón (función lineal + activación), funciones de activación (ReLU, GELU), positional encoding (seno/coseno), RNN (tanh, sigmoide), atención (softmax).

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Iris (clasificación de flores).
- **Actividades:**
  1. Cargar el dataset y explorar sus dimensiones.
  2. Visualizar las distribuciones de cada característica usando histogramas.
  3. Ajustar manualmente (por ensayo y error) una función lineal que separe dos clases y visualizar la frontera.

---

## Semana 2: Fundamentos de IA

### Propósito
Comprender la estructura general de un modelo de IA, los tipos de aprendizaje, y cómo los conceptos matemáticos se integran en el flujo de trabajo de machine learning.

### Notebook Conceptual (NB1) – Estructura de un Modelo de IA

- **Datos:** Datos sintéticos para regresión, clasificación y clustering.
- **Actividades:**
  1. Definir la estructura general de un modelo: $f(x;\theta)$ (modelo), $L(\theta)$ (función de pérdida), optimización.
  2. Visualizar diferentes tipos de funciones de pérdida según el problema:
     - Regresión: MSE (distancia entre números)
     - Clasificación: Cross Entropy (diferencia entre probabilidades)
     - Clustering: SSE (compactación de clusters)
     - SVM: Hinge Loss (margen geométrico)
  3. Implementar el flujo completo para un problema simple: definir modelo, calcular predicción, pérdida, optimizar.
  4. Comparar optimizadores: closed-form (regresión lineal), gradient descent, SGD.
  5. Simular Empirical Risk Minimization (ERM): $\min_\theta \frac{1}{n}\sum l(y_i,f(x_i;\theta))$.
  6. Discutir regularización como parte de la función objetivo: $L(\theta) = Loss + \lambda R(\theta)$.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML/RL:** Regresión (MSE), clasificación (log-loss), clustering (SSE), árboles (Gini, entropía).
  - **DL:** Backpropagation, optimizadores (SGD, Adam, RMSProp).
  - **Insight clave:** Toda rama de ML cambia solo tres cosas: el modelo, la pérdida y el optimizador.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Boston Housing (regresión) y Titanic (clasificación).
- **Actividades:**
  1. Implementar regresión lineal con closed-form y con gradient descent.
  2. Implementar regresión logística con cross entropy y SGD.
  3. Comparar tiempos de entrenamiento y resultados.

---

## Semana 3: Matrices

### Propósito
Dominar la estructura de datos fundamental en IA: la matriz, y entender cómo se organiza la información en diferentes dominios.

### Notebook Conceptual (NB1) – Manipulación de Matrices

- **Datos:** Matrices creadas con NumPy de diferentes dimensiones.
- **Actividades:**
  1. Creación de matrices cuadradas, diagonales, identidad, triangulares.
  2. Operaciones: suma, resta, multiplicación por escalar.
  3. Producto de matrices y multiplicación matriz-vector.
  4. Transposición.
  5. Cálculo de determinante, inversa, rango.
  6. Representación de datasets como matrices: filas = muestras, columnas = features.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Matriz de covarianza, regresión lineal (representación matricial $X\beta = y$), solución normal $\hat{\beta} = (X^TX)^{-1}X^Ty$, PCA, sistemas de recomendación (factorización matricial).
  - **DL:** Pesos como matrices en capas lineales ($\mathbf{W}\mathbf{x} + \mathbf{b}$), backpropagation (operaciones matriciales), inicialización de pesos, convoluciones, Transformers (multiplicación de matrices en atención).

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** California Housing.
- **Actividades:**
  1. Representar el dataset como matriz de features $X$ y vector objetivo $y$.
  2. Implementar regresión lineal usando la ecuación normal.
  3. Calcular la matriz de covarianza de las features.

---

## Semana 4: Sistemas de Ecuaciones Lineales

### Propósito
Conectar la resolución de sistemas lineales con el primer modelo de machine learning: la regresión lineal.

### Notebook Conceptual (NB1) – Resolviendo Sistemas

- **Datos:** Sistemas de ecuaciones lineales generados (2x2, 3x3) y sistemas sobredeterminados.
- **Actividades:**
  1. Representación de sistemas lineales como $Ax = b$.
  2. Interpretación geométrica: intersección de rectas/planos.
  3. Resolver sistemas cuadrados con eliminación gaussiana y con `np.linalg.solve`.
  4. Plantear un sistema sobredeterminado: $X\beta = y$ con más ecuaciones que incógnitas.
  5. Encontrar la solución por mínimos cuadrados: $\beta = (X^T X)^{-1}X^T y$.
  6. Identificar sistemas con solución única, infinitas soluciones o inconsistentes.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Regresión lineal (mínimos cuadrados, ecuación normal). La función de coste MSE: $J(\beta) = \frac{1}{n}\sum (y_i - \hat{y}_i)^2$ es la base de la optimización.
  - **DL:** Base conceptual para optimización, subyace en problemas de ajuste.
  - **RL:** En robótica, los sistemas de ecuaciones lineales modelan la cinemática de brazos robóticos.
  - **CV:** Transformaciones geométricas (rotación, traslación) se representan como sistemas lineales.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** California Housing.
- **Actividades:**
  1. Implementar la ecuación normal desde cero con NumPy para encontrar los coeficientes de regresión.
  2. Comparar con `sklearn.linear_model.LinearRegression`.
  3. Evaluar el modelo con MSE y R².

---

## Semana 5: Espacios Vectoriales y Normas

### Propósito
Comprender los conceptos fundamentales de espacios vectoriales, normas y distancias, que son la base de muchos algoritmos de ML.

### Notebook Conceptual (NB1) – Explorando Espacios y Normas

- **Datos:** Puntos en ℝ², ℝ³ generados aleatoriamente.
- **Actividades:**
  1. Visualizar vectores en el plano y sus combinaciones lineales.
  2. Concepto de independencia lineal y base.
  3. Calcular producto punto, ángulo entre vectores y similitud coseno.
  4. Implementar normas L1, L2, L∞ y visualizar las bolas unitarias.
  5. Calcular distancias: euclidiana, Manhattan, Chebyshev.
  6. Visualizar proyecciones ortogonales.
  7. Definir rectas, planos e hiperplanos; semiespacios.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Regularización Ridge (L2) y Lasso (L1), KNN (distancias), SVM (producto punto, margen), clustering (distancias, silhouette), sistemas de recomendación (similitud coseno), Huber loss.
  - **DL:** Regularización en redes (normas de pesos), LoRA (normas de matrices), atención (producto punto Q·K), RAG (búsqueda de vecinos, distancias), CLIP (similitud coseno).

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** MNIST (dígitos escritos a mano).
- **Actividades:**
  1. Calcular la imagen promedio de cada dígito.
  2. Para un dígito dado, encontrar los 5 más similares usando similitud de coseno.
  3. Implementar un clasificador k-NN usando distancias.

---

## Semana 6: Transformaciones Lineales

### Propósito
Entender que las capas de una red neuronal son transformaciones lineales que deforman el espacio para hacer los datos separables.

### Notebook Conceptual (NB1) – Transformando el Espacio

- **Datos:** Nube de puntos 2D formando dos círculos concéntricos (no linealmente separables).
- **Actividades:**
  1. Definir transformación lineal y su representación matricial.
  2. Visualizar el efecto de transformaciones lineales (rotación, escalado, cizallamiento) aplicadas por una matriz $W$.
  3. Mostrar que una transformación lineal NO puede separar los círculos concéntricos.
  4. Composición de transformaciones.
  5. Introducir la no-linealidad (ReLU) después de la transformación y observar cómo ahora es posible separar.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Feature engineering, regresión lineal (transformación lineal), SVM con kernel (mapeo a espacio de características).
  - **DL:** Cada capa de una red es $\mathbf{h} = \sigma(\mathbf{W}\mathbf{x} + \mathbf{b})$. Capas lineales, redes profundas como composición de transformaciones, kernel en CNN, compresión y representación de audio, imágenes, video y datos.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Fashion-MNIST.
- **Actividades:**
  1. Visualizar las imágenes en 2D usando PCA.
  2. Discutir por qué se necesita una red profunda para clasificar correctamente.

---

## Semana 7: Autovalores y Autovectores

### Propósito
Descubrir que los autovectores encuentran las direcciones de máxima varianza, la base del Análisis de Componentes Principales (PCA).

### Notebook Conceptual (NB1) – Autovectores

- **Datos:** Nube de puntos 2D con correlación (elipsoide alargado).
- **Actividades:**
  1. Definición de autovalor y autovector: $A\mathbf{v} = \lambda\mathbf{v}$.
  2. Calcular la matriz de covarianza de los datos.
  3. Calcular autovalores ($\lambda$) y autovectores ($\mathbf{v}$) con `np.linalg.eig`.
  4. Visualizar los autovectores sobre la nube de puntos: el primero apunta en la dirección de máxima varianza.
  5. Ecuación característica y diagonalización.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML/CV:** PCA proyecta los datos sobre los autovectores de la matriz de covarianza para reducir dimensionalidad. La varianza explicada por cada componente es su autovalor.
  - **NLP:** Latent Semantic Analysis (LSA) usa SVD (relacionado con autovalores) para encontrar temas en documentos.
  - **GenAI:** Los modelos generativos a menudo operan en espacios latentes donde los autovectores pueden representar direcciones de interpretación.
  - **RL:** PageRank de Google es un problema de autovectores.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** MNIST.
- **Actividades:**
  1. Implementar PCA desde cero usando autovalores/autovectores.
  2. Proyectar los dígitos a 2D y visualizarlos.
  3. Comparar con `sklearn.decomposition.PCA`.

---

## Semana 8: Descomposición de Matrices (SVD)

### Propósito
Descubrir la descomposición más poderosa y estable del álgebra lineal, con aplicaciones que van desde la compresión hasta los sistemas de recomendación.

### Notebook Conceptual (NB1) – SVD con Datos Dummy

- **Datos:** Matriz pequeña (ej. 5x5) y una imagen en escala de grises.
- **Actividades:**
  1. Descomponer una matriz $A$ en $U \Sigma V^T$ usando `np.linalg.svd`.
  2. Interpretar $U$, $\Sigma$ (valores singulares) y $V^T$.
  3. Reconstruir la matriz usando solo los primeros $k$ valores singulares (aproximación de bajo rango).
  4. Aplicar a una imagen: comprimirla manteniendo solo el 10% de los valores singulares y visualizar la pérdida de calidad.
  5. Calcular la pseudoinversa de Moore-Penrose.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML/CV:** Compresión de imágenes y reducción de ruido.
  - **RecSys:** Filtrado colaborativo (ej. Netflix Prize) descompone la matriz usuario-producto en factores latentes.
  - **NLP:** Latent Semantic Analysis (LSA) usa SVD para encontrar relaciones término-documento.
  - **DL:** LoRA (descomposición de bajo rango), compresión de modelos, análisis semántico latente.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** MovieLens (pequeño) de ratings de películas.
- **Actividades:**
  1. Construir la matriz usuario-película (con NaN para ratings no vistos).
  2. Aplicar SVD para completar la matriz (predecir ratings).
  3. Hacer recomendaciones para un usuario basadas en las predicciones.

---

## Semana 9: Tensores

### Propósito
Dominar la estructura de datos fundamental en deep learning: el tensor, y entender cómo se organiza la información en diferentes dominios.

### Notebook Conceptual (NB1) – Manipulación de Tensores

- **Datos:** Tensores creados con NumPy y PyTorch de diferentes dimensiones (0D a 4D).
- **Actividades:**
  1. Creación de escalares (0D), vectores (1D), matrices (2D) y tensores 3D y 4D.
  2. Operaciones tensoriales: suma, multiplicación elemento a elemento.
  3. Broadcasting: reglas para operar tensores de diferentes formas.
  4. Reorganización: reshape, transpose, permute, squeeze, unsqueeze.
  5. Producto punto generalizado con `einsum`.
  6. Representación de datos multidimensionales: imágenes (alto, ancho, canales), secuencias (batch, tiempo, features), lotes (batch).
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Reducción de dimensionalidad con SVD o PCA, one-hot encoding.
  - **DL:**
    - **CNN:** Tensores 4D (Batch, Canales, Altura, Ancho)
    - **Embeddings:** Conversión de palabras en vectores densos
    - **RNN/LSTM:** Tensores 3D (Batch, Timesteps, Features)
    - **Transformers:** Tensores 3D (batch, secuencia, embedding)
    - **Vision Transformers:** Parcheo de imágenes
    - **Transfer Learning:** Congelación de "rebanadas" de tensores

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** CIFAR-10 (imágenes a color de 32x32).
- **Actividades:**
  1. Cargar el dataset y verificar su forma (50000, 32, 32, 3) como tensor 4D.
  2. Extraer un canal de color (tensor 3D) y visualizarlo.
  3. Aplicar reshape y transpose para modificar el orden de dimensiones.

---

## Semana 10: Probabilidad y Estadística para IA

### Propósito
Comprender los fundamentos probabilísticos y estadísticos que subyacen a los modelos de IA, desde la inferencia hasta la evaluación.

### Notebook Conceptual (NB1) – Probabilidad y Estadística

- **Datos:** Datos simulados con distribuciones conocidas (normal, Bernoulli, uniforme).
- **Actividades:**
  1. Probabilidad básica: axiomas, probabilidad condicional, independencia.
  2. Teorema de Bayes: visualización y aplicación.
  3. Variables aleatorias, esperanza, varianza, covarianza.
  4. Distribuciones: normal, Bernoulli, multinomial.
  5. Estadística descriptiva: media, mediana, moda, desviación estándar, cuartiles, correlación.
  6. Entropía, información mutua, divergencia KL.
  7. Tests estadísticos: Kolmogorov–Smirnov, PSI, p-valor.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** EDA, regresión logística (probabilidad), Naive Bayes (teorema de Bayes), árboles (entropía, Gini), bias-varianza, PCA (covarianza), series de tiempo (autocorrelación), RANSAC, Adjusted Rand Index, Shapley, tests A/B.
  - **DL:** Dropout (Bernoulli), inicialización (varianza), Batch Norm, modelos de lenguaje (probabilidad de secuencias), modelos generativos (distribuciones, KL), CLIP (softmax, pérdida contrastiva).

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Titanic o cualquier dataset de clasificación.
- **Actividades:**
  1. Realizar EDA completo con estadística descriptiva.
  2. Calcular correlaciones entre features.
  3. Entrenar un clasificador y evaluar con diferentes métricas.

---

## Semana 11: Límites y Continuidad

### Propósito
Entender por qué las funciones "suaves" (diferenciables) son esenciales para el entrenamiento de modelos.

### Notebook Conceptual (NB1) – Explorando Límites

- **Datos:** Funciones simbólicas con SymPy y NumPy.
- **Actividades:**
  1. Concepto de límite (intuitivo y formal básico).
  2. Continuidad de funciones, tipos de discontinuidades.
  3. Visualización de discontinuidades: función escalón, función parte entera.
  4. Comparación con funciones continuas a trozos como ReLU.
  5. Teorema del valor intermedio.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Funciones de pérdida (necesidad de continuidad para optimización), optimización (convergencia).
  - **DL:** Estabilidad de funciones de activación, convergencia de entrenamiento. ReLU es diferenciable excepto en 0, pero se maneja con subgradientes.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Actividades:**
  1. Ejercicios de límites con SymPy.
  2. Discutir por qué la función de pérdida "0-1 loss" no es útil para optimización basada en gradientes.

---

## Semana 12: Derivadas e Integrales en una Variable

### Propósito
Comprender que la derivada es la herramienta que le dice al modelo cómo ajustar sus parámetros para minimizar el error, y la integral conecta con métricas clave como AUC.

### Notebook Conceptual (NB1) – Derivadas e Integrales

- **Datos:** Funciones simples ($f(x)=x^2$, $f(x)=e^x$, $f(x)=\ln x$, sigmoide, tanh).
- **Actividades:**
  1. Derivada como tasa de cambio, interpretación geométrica.
  2. Reglas de derivación (producto, cociente, cadena).
  3. Derivada de funciones elementales y de activación.
  4. Derivada de la función de pérdida MSE: $\frac{\partial MSE}{\partial w} = \frac{2}{n}\sum -x_i(y_i - \hat{y}_i)$.
  5. Integral definida como área bajo la curva.
  6. Teorema fundamental del cálculo.
  7. Cálculo de AUC mediante integración numérica.
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Derivadas para gradiente en regresión, derivada de sigmoide y log-loss, AUC (integral), integrales en probabilidades.
  - **DL:** Derivadas en backpropagation (regla de la cadena), derivadas de funciones de activación, pérdidas basadas en integrales (cross-entropy).

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Titanic.
- **Actividades:**
  1. Entrenar un clasificador (regresión logística).
  2. Calcular la curva ROC y el AUC manualmente (integrando) y con `sklearn.metrics.roc_auc_score`.

---

## Semana 13: Cálculo Multivariable

### Propósito
Entender que el gradiente es un vector que apunta en la dirección de máximo crecimiento y que su negativo es la dirección de descenso, y cómo la regla de la cadena permite propagar errores en redes profundas.

### Notebook Conceptual (NB1) – Visualizando el Gradiente

- **Datos:** Función de coste 2D: $J(w_1, w_2) = w_1^2 + w_2^2$ (convexa) y función con punto silla.
- **Actividades:**
  1. Funciones de varias variables, representación y visualización.
  2. Derivadas parciales.
  3. Vector gradiente $\nabla J = [\frac{\partial J}{\partial w_1}, \frac{\partial J}{\partial w_2}]$, interpretación geométrica.
  4. Visualizar el gradiente como flechas sobre un mapa de contorno.
  5. Regla de la cadena multivariable aplicada a una red pequeña.
  6. Matriz Jacobiana y Hessiana (introducción).
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Gradiente de funciones de costo con múltiples parámetros, gradiente de log-loss, superficie de pérdida.
  - **DL:** Backpropagation (regla de la cadena multivariable), gradiente en redes profundas, gradiente evanescente/explosivo (producto de Jacobianos), optimizadores (Adam, etc.).
  - **CV:** El gradiente de una imagen (filtros Sobel, Canny) se usa para detección de bordes.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** Boston Housing.
- **Actividades:**
  1. Calcular el gradiente del MSE para todos los coeficientes.
  2. Visualizar la magnitud del gradiente a lo largo de las épocas.

---

## Semana 14: Optimización y Gradiente Descendente

### Propósito
Liberarse de derivar a mano y comprender cómo las librerías modernas automatizan el cálculo de gradientes, y dominar los diferentes optimizadores usados en ML y DL.

### Notebook Conceptual (NB1) – Gradiente Automático y Optimizadores

- **Datos:** Datos sintéticos para regresión lineal (con ruido).
- **Actividades:**
  1. Funciones cóncavas, convexas; máximos y mínimos locales y globales.
  2. Implementar descenso de gradiente **desde cero** con NumPy.
  3. Implementar el mismo modelo con PyTorch usando `autograd` y optimizadores.
  4. Experimentar con diferentes **tasas de aprendizaje** ($\eta$).
  5. Comparar variantes: **Batch GD**, **Stochastic GD** (SGD), **Mini-batch GD**.
  6. Probar optimizadores: Momentum, Adam, RMSProp.
  7. Programación de learning rate (step decay, cosine annealing).
  8. Regularización como penalización en la función objetivo (L1, L2).
- **Conexiones IA (Ecuaciones y Ramas):**
  - **ML:** Descenso de gradiente en regresión y clasificación, gradient boosting, búsqueda de hiperparámetros.
  - **DL:** PyTorch y TensorFlow usan diferenciación automática. SGD, Momentum, Adam, AdamW, cosine annealing. Fine-tuning de LLMs (GPT, LLaMA) usa los mismos principios.
  - **RL:** Algoritmos de Deep Q-Learning usan gradiente descendente.

### Notebook de Ejercicios (NB2) – Dataset Real

- **Dataset:** MNIST.
- **Actividades:**
  1. Entrenar una regresión logística con PyTorch.
  2. Visualizar la pérdida y la accuracy en entrenamiento y validación.
  3. Probar diferentes optimizadores (SGD, Adam, RMSProp) y learning rates.
  4. Comparar resultados y discutir cuándo usar cada optimizador.

---

## Metodología y Evaluación

### Estrategias metodológicas
- **Clases síncronas:** Exposición conceptual con diapositivas y programación en vivo con los notebooks conceptuales, destacando siempre la sección "Conexiones IA".
- **Trabajo asíncrono:** Resolución de los notebooks de ejercicios sobre datasets reales, lecturas complementarias y pequeños retos.
- **Aprendizaje activo:** Discusión de aplicaciones reales, ejercicios de entrevistas técnicas donde se pregunte por el fundamento matemático.

### Materiales educativos
- Cuadernos de Jupyter (NB1 y NB2) para cada semana.
- Acceso a Google Colab con GPU para las semanas de PyTorch.
- Bibliografía: Strang, Deisenroth, Goodfellow, documentación de NumPy/SciPy/PyTorch.

### Evaluación
- **Evaluaciones continuas (EC):** Entrega de notebooks de ejercicios (40%).
- **Examen parcial (EP):** Proyecto individual que integre Semanas 1-7 (30%).
- **Examen final (EF):** Proyecto final que integre todo el curso (30%).