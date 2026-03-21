## Semana 2: Fundamentos de IA

### Teoría

#### 1. ¿Qué es la Inteligencia Artificial? Definiciones y alcance

La Inteligencia Artificial (IA) es un campo de la informática que busca crear sistemas capaces de realizar tareas que requieren inteligencia humana. Estas tareas incluyen el aprendizaje, el razonamiento, la percepción, la comprensión del lenguaje natural y la toma de decisiones.

**Definiciones clave:**
- **IA estrecha (débil):** Sistemas diseñados para tareas específicas (ej. reconocimiento facial, recomendaciones).
- **IA general (fuerte):** Sistemas con inteligencia similar a la humana, capaces de realizar cualquier tarea intelectual (aún no alcanzada).
- **IA superinteligente:** Hipotética IA que supera la inteligencia humana en todos los aspectos.

**Alcance en el curso:** Nos enfocaremos en las técnicas matemáticas y computacionales que permiten construir modelos de aprendizaje automático (Machine Learning) y aprendizaje profundo (Deep Learning), que son las ramas más exitosas de la IA actual.

#### 2. Tipos de aprendizaje

| Tipo | Descripción | Ejemplo |
|------|-------------|---------|
| **Supervisado** | El modelo aprende de datos etiquetados: pares (entrada, salida deseada). | Clasificación de correos como spam/no spam con etiquetas. |
| **No supervisado** | El modelo encuentra patrones en datos no etiquetados. | Segmentación de clientes en grupos con comportamientos similares. |
| **Por refuerzo** | El agente aprende a través de interacciones con un entorno, recibiendo recompensas o castigos. | Un programa que aprende a jugar al ajedrez mediante prueba y error. |

**Ejemplos concretos:**
- **Supervisado:** Predecir el precio de una casa (regresión) o diagnosticar una enfermedad a partir de síntomas (clasificación).
- **No supervisado:** Agrupar artículos de noticias por temas (clustering) o reducir la dimensionalidad de datos para visualización (PCA).
- **Por refuerzo:** Entrenar un robot para caminar o un agente para jugar videojuegos.

#### 3. Estructura general de un modelo de IA

Todo modelo de IA (ya sea de ML o DL) puede entenderse mediante tres componentes fundamentales:

1. **Función de predicción:** \( \hat{y} = f(x; \theta) \)
   - \(x\): entrada (datos, características)
   - \(\theta\): parámetros del modelo (lo que se aprende)
   - \(\hat{y}\): predicción del modelo

2. **Función de pérdida:** \( L(\theta) \)
   - Mide qué tan lejos están las predicciones \(\hat{y}\) de los valores reales \(y\) (si existen).
   - **La pérdida define qué significa equivocarse.**

3. **Optimización:** \( \min_{\theta} L(\theta) \)
   - Proceso de encontrar los parámetros \(\theta\) que minimizan la pérdida.
   - **El optimizador define cómo corregir el error.**

**Flujo típico:**
1. Definir el modelo \(f(x;\theta)\).
2. Para un dato \(x_i\), obtener predicción \(\hat{y}_i\).
3. Calcular la pérdida individual \(\ell(y_i, \hat{y}_i)\).
4. Calcular la pérdida total sobre todo el conjunto: \(L(\theta) = \frac{1}{n}\sum_{i=1}^n \ell(y_i, \hat{y}_i)\).
5. Aplicar un algoritmo de optimización para actualizar \(\theta\) y reducir \(L(\theta)\).
6. Repetir hasta convergencia.

#### 4. Ejemplos de problemas

| Problema | Descripción | Tipo de aprendizaje |
|----------|-------------|---------------------|
| **Regresión** | Predecir un valor numérico continuo (ej. precio, temperatura). | Supervisado |
| **Clasificación** | Asignar una categoría a una entrada (ej. spam/no spam, dígito manuscrito). | Supervisado |
| **Clustering** | Agrupar datos similares sin etiquetas previas (ej. segmentación de clientes). | No supervisado |
| **Generación** | Crear nuevos datos similares a los de entrenamiento (ej. imágenes, texto). | No supervisado / semi-supervisado |

#### 5. Motivación de las herramientas matemáticas

- **Álgebra lineal:** Para representar datos (vectores, matrices, tensores), transformaciones (capas de redes), operaciones eficientes (producto punto, proyecciones).
- **Cálculo:** Para entender tasas de cambio, optimizar funciones de pérdida (gradientes, regla de la cadena).
- **Probabilidad y estadística:** Para modelar incertidumbre, evaluar modelos, entender distribuciones de datos, y fundamentar técnicas como máxima verosimilitud o regularización.

#### 6. Panorama del curso

| Semana | Tema | Conceptos matemáticos | Aplicaciones en IA |
|--------|------|----------------------|--------------------|
| 1 | Fundamentos Matemáticos | Notación, funciones, sumatorias, objetos matemáticos | Regresión, funciones de activación, pérdidas |
| 2 | Fundamentos de IA | Estructura de modelos, tipos de aprendizaje, pérdidas, optimización | Visión global de ML y DL |
| 3 | Matrices | Operaciones, propiedades, representación de datos | Regresión lineal, capas de redes |
| 4 | Sistemas de ecuaciones lineales | Mínimos cuadrados, sistemas sobredeterminados | Regresión lineal, solución analítica |
| 5 | Espacios vectoriales y normas | Vectores, normas, distancias, producto punto, hiperplanos | KNN, SVM, regularización, clustering |
| 6 | Transformaciones lineales | Composiciones, proyecciones, rotaciones | Capas de redes, kernels |
| 7 | Autovalores y autovectores | Diagonalización, descomposición espectral | PCA, análisis de covarianza |
| 8 | Descomposición de matrices (SVD) | SVD, pseudoinversa, bajo rango | Sistemas de recomendación, compresión, LoRA |
| 9 | Tensores | Operaciones, broadcasting, reshape | CNNs, RNNs, Transformers |
| 10 | Probabilidad y estadística | Bayes, distribuciones, entropía, tests | Naive Bayes, árboles, métricas, A/B testing |
| 11 | Límites y continuidad | Continuidad, estabilidad | Funciones de pérdida, convergencia |
| 12 | Derivadas e integrales (1D) | Reglas de derivación, integrales, AUC | Gradiente, backprop, AUC |
| 13 | Cálculo multivariable | Derivadas parciales, gradiente, Jacobiano, Hessiano | Backprop, optimización, superficies de pérdida |
| 14 | Optimización y gradiente descendente | SGD, Momentum, Adam, regularización | Entrenamiento de modelos ML/DL |

---

### Aplicaciones prácticas

#### 1. Ideas matemáticas de funciones de pérdida

Las funciones de pérdida se basan en tres conceptos fundamentales: **distancia**, **probabilidad** y **margen geométrico**.

##### a) Distancia entre números (regresión)

- **MSE (Mean Squared Error):** Mide el promedio de los cuadrados de los errores.
  \[
  \text{MSE} = \frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2
  \]
  **Ejemplo paso a paso:**
  Valores reales: \(y = [3, -0.5, 2, 7]\)  
  Predicciones: \(\hat{y} = [2.5, 0.0, 2, 8]\)  
  Errores: \([0.5, -0.5, 0, -1]\)  
  Cuadrados: \([0.25, 0.25, 0, 1]\)  
  Suma: \(1.5\)  
  MSE = \(1.5 / 4 = 0.375\)

- **MAE (Mean Absolute Error):** Promedio de errores absolutos.
  \[
  \text{MAE} = \frac{1}{n}\sum_{i=1}^{n} |y_i - \hat{y}_i|
  \]
  Con los mismos datos: \(|0.5| + | -0.5| + |0| + | -1| = 0.5 + 0.5 + 0 + 1 = 2\), MAE = \(2/4 = 0.5\).

- **K-means (pérdida SSE):** En clustering, la pérdida es la suma de distancias al cuadrado de cada punto a su centroide.
  \[
  \text{SSE} = \sum_{k=1}^{K} \sum_{x \in C_k} \|x - \mu_k\|^2
  \]
  donde \(\mu_k\) es el centroide del cluster \(C_k\).

##### b) Probabilidad (clasificación)

- **Log-loss (entropía cruzada binaria):** Mide la discrepancia entre la probabilidad predicha y la etiqueta real.
  \[
  L = -\frac{1}{n}\sum_{i=1}^{n} \left[ y_i \log(\hat{y}_i) + (1-y_i) \log(1-\hat{y}_i) \right]
  \]
  **Ejemplo paso a paso:**
  Para un solo ejemplo con \(y=1\) y \(\hat{y}=0.8\):
  \(L_i = -[1 \cdot \log(0.8) + 0 \cdot \log(0.2)] = -\log(0.8) \approx -(-0.2231) = 0.2231\)  
  Para \(y=0\) y \(\hat{y}=0.1\):
  \(L_i = -[0 \cdot \log(0.1) + 1 \cdot \log(0.9)] = -\log(0.9) \approx 0.1054\)

- **Cross-entropy multiclase:** Para \(K\) clases, con etiquetas one-hot \(y \in \{0,1\}^K\) y probabilidades predichas \(\hat{y}_k\):
  \[
  L = -\sum_{k=1}^{K} y_k \log(\hat{y}_k)
  \]
  donde \(\hat{y}_k = \frac{e^{z_k}}{\sum_{j=1}^{K} e^{z_j}}\) (softmax).

##### c) Margen geométrico (SVM)

- **Hinge Loss:** Utilizada en SVM para clasificación binaria. Busca que los puntos estén al menos a una distancia de 1 del hiperplano de separación.
  \[
  L = \max(0, 1 - y \cdot \hat{y})
  \]
  donde \(y \in \{-1, 1\}\) y \(\hat{y} = w^T x + b\) es la salida del modelo (sin activación).  
  **Interpretación:** Si \(y \cdot \hat{y} \geq 1\), la pérdida es 0 (punto bien clasificado y con margen suficiente). Si no, la pérdida crece linealmente.

#### 2. Optimización: minimizar \(L(\theta)\)

La mayoría de los problemas de ML se formulan como:
\[
\min_{\theta} L(\theta)
\]
donde \(L(\theta)\) es una función de costo (pérdida promediada sobre el conjunto de datos):
\[
L(\theta) = \frac{1}{n}\sum_{i=1}^{n} \ell(y_i, f(x_i;\theta))
\]

**Ejemplo concreto:** Para regresión lineal con MSE, tenemos:
\[
L(w,b) = \frac{1}{n}\sum_{i=1}^{n} (y_i - (w^T x_i + b))^2
\]
Queremos encontrar \(w\) y \(b\) que minimicen \(L\).

#### 3. Flujo típico de entrenamiento

1. **Definir modelo:** \(f(x;\theta)\)
2. **Obtener predicción:** \(\hat{y} = f(x;\theta)\)
3. **Calcular pérdida individual:** \(\ell(y, \hat{y})\)
4. **Calcular pérdida total:** \(L(\theta) = \frac{1}{n}\sum \ell(y_i, \hat{y}_i)\)
5. **Elegir algoritmo de optimización** (gradiente descendente, Adam, etc.)
6. **Actualizar parámetros:** \(\theta \leftarrow \theta - \eta \nabla L(\theta)\) (para gradiente descendente)
7. **Repetir** hasta convergencia.

**Ejemplo con regresión lineal (una variable):**
- Modelo: \(\hat{y} = wx + b\)
- Pérdida MSE: \(L(w,b) = \frac{1}{n}\sum (y_i - (wx_i + b))^2\)
- Gradientes:
  \[
  \frac{\partial L}{\partial w} = -\frac{2}{n}\sum x_i (y_i - (wx_i + b))
  \]
  \[
  \frac{\partial L}{\partial b} = -\frac{2}{n}\sum (y_i - (wx_i + b))
  \]
- Actualización: \(w \leftarrow w - \eta \frac{\partial L}{\partial w}\), \(b \leftarrow b - \eta \frac{\partial L}{\partial b}\)

#### 4. Formas de optimización

| Método | Descripción | Uso típico |
|--------|-------------|------------|
| **Fórmula analítica (closed-form)** | Solución directa mediante álgebra lineal, ej. regresión lineal: \(\theta = (X^T X)^{-1} X^T y\) | ML clásico, datasets pequeños |
| **Gradiente descendente** | Iterativo, usa derivadas para actualizar parámetros | ML y DL, datasets grandes |
| **SGD (Stochastic Gradient Descent)** | Gradiente calculado con un solo ejemplo (o mini-batch) por iteración | Datasets muy grandes, online learning |
| **Adam** | Optimizador adaptativo con momentos | Deep Learning (estándar) |
| **EM (Expectation-Maximization)** | Algoritmo para modelos con variables latentes | Clustering (ej. mezclas gaussianas) |

**Ejemplo de un paso de gradiente descendente:**
Supongamos \(L(\theta) = \theta^2\) (una parábola simple). Queremos minimizar.  
- Iniciamos \(\theta = 3\), \(\eta = 0.1\).  
- Gradiente: \(L'(\theta) = 2\theta = 6\).  
- Actualización: \(\theta_{\text{nuevo}} = 3 - 0.1 \times 6 = 2.4\).  
- Repetir hasta converger a 0.

#### 5. Diferencias de optimización en ML y DL

- **ML clásico:** Muchos modelos tienen soluciones analíticas (regresión lineal) o algoritmos específicos (SVM con SMO, árboles con greedy). El gradiente se usa pero en problemas convexos.
- **Deep Learning:** Las funciones de pérdida son no convexas y con millones de parámetros. Se usa **backpropagation** para calcular gradientes eficientemente mediante la regla de la cadena. Optimizadores como Adam son estándar.

**Backpropagation en una red simple:**  
Para una red con una capa oculta:
\[
\hat{y} = \sigma(W_2 \cdot \sigma(W_1 x + b_1) + b_2)
\]
El gradiente de la pérdida respecto a cada peso se calcula aplicando la regla de la cadena desde la salida hacia atrás.

#### 6. Tabla: Tipo de problema vs qué mide la pérdida

| Tipo problema | Qué mide la pérdida             | Ejemplo de pérdida |
|---------------|----------------------------------|---------------------|
| Regresión     | distancia entre números         | MSE, MAE            |
| Clasificación | diferencia entre probabilidades | Cross-entropy, Hinge Loss |
| Clustering    | compactación de clusters        | SSE (K-means)       |
| Deep Learning | cualquiera de las anteriores    | Según la tarea      |
| Reinforcement | error de estimación de valor    | Temporal Difference (TD) error |

#### 7. Tabla: Métodos de optimización

| Método                            | Dónde se usa     | Fórmula de actualización (simplificada) |
|-----------------------------------|------------------|------------------------------------------|
| Gradient Descent                  | ML clásico y DL  | \(\theta \leftarrow \theta - \eta \nabla L(\theta)\) |
| Stochastic Gradient Descent (SGD) | datasets grandes | \(\theta \leftarrow \theta - \eta \nabla L_i(\theta)\) (con un ejemplo) |
| Adam                              | Deep Learning    | Adaptativo con momentos de primer y segundo orden |
| Closed-form solution              | regresión lineal | \(\theta = (X^T X)^{-1} X^T y\) |
| EM Algorithm                      | clustering       | Iteraciones E-step y M-step |

#### 8. Interpretaciones de términos

| Término            | Significado exacto                                           |
| ------------------ | ------------------------------------------------------------ |
| Loss function      | error **por ejemplo individual**                             |
| Cost function      | promedio o suma del error en el **dataset**                  |
| Objective function | función total que se optimiza (puede incluir regularización) |

**Nota:** En la práctica muchos autores usan \(L(\theta)\) para todo, pero es importante distinguir conceptualmente.

#### 9. Regularización (parte de la función objetivo)

Para evitar sobreajuste, se añade un término de regularización:
\[
L(\theta) = \text{Loss} + \lambda R(\theta)
\]
**Ejemplo:** Ridge regression (L2):
\[
L = \frac{1}{n}\sum (y_i - \hat{y}_i)^2 + \lambda \|\theta\|_2^2
\]
donde \(\|\theta\|_2^2 = \sum \theta_j^2\).

#### 10. Resumen conceptual unificado

Todos los modelos de ML siguen esta estructura:

| Paso | Concepto              |
| ---- | --------------------- |
| 1    | Modelo: \(f(x;\theta)\)  |
| 2    | Pérdida: \(\ell(y,\hat{y})\) |
| 3    | Objetivo: \(L(\theta) = \frac{1}{n}\sum \ell(y_i, f(x_i;\theta))\) |
| 4    | Optimización: \(\min_\theta L(\theta)\) |

Esta formulación se conoce como **Empirical Risk Minimization (ERM)**.

#### 11. Idea clave

Toda rama de ML cambia solo estas tres cosas:

| Elemento     | Qué cambia    |
| ------------ | ------------- |
| Modelo       | \(f(x;\theta)\) |
| Pérdida      | \(\ell(y,\hat{y})\) |
| Optimización | Algoritmo de actualización |

---
