## Semana 1 — Fundamentos Matemáticos I: Funciones y Modelamiento

**Objetivo:** Construir el lenguaje matemático necesario para representar datos y modelos en inteligencia artificial. Al finalizar esta semana, el estudiante será capaz de comprender y utilizar la notación matemática básica, identificar diferentes tipos de funciones, y relacionar estos conceptos con la formulación de problemas de machine learning, incluyendo funciones de pérdida, optimización y la estructura general de un modelo.

---

### 1. Notación Matemática Básica

#### Índices y subíndices
En matemáticas y en machine learning, usamos índices para referirnos a elementos específicos dentro de un conjunto o secuencia. Por ejemplo:
- \(x_i\) representa el i-ésimo elemento de un vector o conjunto de datos.
- \(w_{ij}\) puede ser el peso que conecta la neurona i con la neurona j en una red neuronal.

#### Sumatorias y productorias
- **Sumatoria simple:** \(\sum_{i=1}^{n} x_i = x_1 + x_2 + \dots + x_n\)  
  Se usa para acumular valores, por ejemplo, en el cálculo de promedios o en funciones de costo.
- **Sumatoria doble:** \(\sum_{i=1}^{n}\sum_{j=1}^{m} a_{ij}\) suma todos los elementos de una matriz.
- **Productoria:** \(\prod_{i=1}^{n} x_i = x_1 \cdot x_2 \cdots x_n\)  
  Aparece en probabilidades (por ejemplo, la verosimilitud de una muestra independiente).

#### Notación vectorial
Un vector \(\mathbf{x} \in \mathbb{R}^n\) se escribe como \(\mathbf{x} = (x_1, x_2, \dots, x_n)\). En machine learning, los datos suelen representarse como vectores de características.

#### Conjuntos numéricos
- \(\mathbb{R}\): números reales. La mayoría de los parámetros y datos en ML son reales.
- \(\mathbb{C}\): números complejos. Menos comunes en ML básico, pero aparecen en procesamiento de señales y algunas transformadas.

---

### 2. Funciones Básicas

Una función \(f: A \to B\) asigna a cada elemento de un conjunto \(A\) (dominio) un único elemento en \(B\) (codominio). El rango es el conjunto de valores que realmente toma la función.

#### Tipos fundamentales

| Función        | Forma general               | Dominio típico | Rango típico | Ejemplo de uso en IA                          |
|----------------|------------------------------|----------------|--------------|------------------------------------------------|
| Lineal         | \(f(x) = mx + b\)            | \(\mathbb{R}\) | \(\mathbb{R}\) | Modelos de regresión lineal                    |
| Polinomial     | \(f(x) = a_n x^n + \dots + a_0\) | \(\mathbb{R}\) | \(\mathbb{R}\) | Aproximación de curvas, features polinomiales  |
| Exponencial    | \(f(x) = a e^{kx}\)           | \(\mathbb{R}\) | \((0,\infty)\) | Crecimiento, decaimiento, softmax              |
| Logarítmica    | \(f(x) = \log_a x\)           | \((0,\infty)\) | \(\mathbb{R}\) | Transformación de datos, entropía, verosimilitud |

**Ejemplo:** En regresión logística, la probabilidad de una clase se modela con una función logística (sigmoide) que es una combinación de funciones lineales y exponenciales.

---

### 3. Funciones de Activación en Redes Neuronales

Las funciones de activación introducen no linealidades en las redes neuronales, permitiendo que aprendan relaciones complejas.

- **Sigmoide:** \(\sigma(x) = \frac{1}{1+e^{-x}}\)  
  Rango: (0,1). Se usa en capas de salida para probabilidades. Problema: saturación y desvanecimiento del gradiente.
- **Tanh:** \(\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}\)  
  Rango: (-1,1). Centrada en cero, pero también satura.
- **ReLU (Rectified Linear Unit):** \(f(x) = \max(0, x)\)  
  Rango: \([0,\infty)\). Muy usada en capas ocultas por su eficiencia y porque evita la saturación para valores positivos. Variantes: Leaky ReLU, ELU, etc.

---

### 4. Aplicaciones en IA: Modelamiento y Funciones de Pérdida

#### Modelamiento de relaciones entre variables
En inteligencia artificial, buscamos modelos \(f(x;\theta)\) que aproximen relaciones entre variables de entrada \(x\) y salidas \(y\). Los parámetros \(\theta\) se ajustan para minimizar una función de pérdida.

#### Introducción a la optimización
Casi todos los problemas de machine learning se formulan como:
\[
\min_{\theta} L(\theta)
\]
donde \(L\) es la función de pérdida (o costo) y \(\theta\) son los parámetros del modelo.

#### Funciones de pérdida según el objetivo
La pérdida mide qué tan equivocada está la predicción del modelo. Según el tipo de problema, la pérdida tiene diferentes interpretaciones:

1. **Distancia entre números** (regresión):  
   - **MSE (Mean Squared Error):** \(\frac{1}{n}\sum (y_i - \hat{y}_i)^2\)  
   - **MAE (Mean Absolute Error):** \(\frac{1}{n}\sum |y_i - \hat{y}_i|\)

2. **Diferencia entre probabilidades** (clasificación):  
   - **Cross-Entropy / Log Loss:** \(-\sum y_i \log(p_i)\) (para clasificación binaria o multiclase)

3. **Margen geométrico** (máquinas de soporte vectorial):  
   - **Hinge Loss:** \(\max(0, 1 - y_i \hat{y}_i)\) (con \(y_i \in \{-1,1\}\))

4. **Compactación de clusters** (clustering):  
   - **SSE (Sum of Squared Errors):** \(\sum \|x_i - \mu_k\|^2\) (donde \(\mu_k\) es el centroide del cluster)

| Tipo de problema | ¿Qué mide la pérdida?               |
|------------------|--------------------------------------|
| Regresión        | Distancia entre números              |
| Clasificación    | Diferencia entre probabilidades      |
| Clustering       | Compactación de clusters             |
| Deep Learning    | Cualquiera de las anteriores         |
| Reinforcement    | Error de estimación de valor         |

---

### 5. Estructura General de un Problema de Machine Learning

La mayoría de los modelos siguen el esquema **Empirical Risk Minimization (ERM)**:

\[
\min_{\theta} \frac{1}{n}\sum_{i=1}^{n} l\big(y_i, f(x_i; \theta)\big)
\]

- \(f(x; \theta)\): modelo (por ejemplo, una red neuronal, regresión lineal, etc.)
- \(l(y, \hat{y})\): pérdida individual (loss)
- \(\frac{1}{n}\sum l\): costo total (cost function)
- \(L(\theta)\): función objetivo (puede incluir regularización)

**Observación:** Aunque a menudo se usa \(L(\theta)\) para todo, es útil distinguir:
- **Loss function:** error por ejemplo individual.
- **Cost function:** promedio o suma del error en el dataset.
- **Objective function:** función total a optimizar (pérdida + regularización).

---

### 6. Casos Específicos por Tipo de Modelo

#### 6.1 Regresión
- **Modelo típico:** \(\hat{y} = f(x; \theta)\) con \(\theta = (w, b)\) (pesos y sesgo).
- **Pérdida común:** MSE.
- **Optimización:**
  - **Closed form** (ecuaciones normales) para regresión lineal simple.
  - **Gradient Descent** para datasets grandes o modelos no lineales.
  - **SGD (Stochastic Gradient Descent)** para aprendizaje en línea.

#### 6.2 Clasificación
- **Modelo típico:** \(p(y|x; \theta)\) (por ejemplo, regresión logística).
- **Pérdida común:** Cross-entropy.
- **Parámetros:** \(\theta = (w, b)\) (aunque el modelo produce probabilidades).
- **Optimización:** Gradient Descent, LBFGS, SGD.

#### 6.3 Clustering (no supervisado)
- **Modelo:** asigna cada punto a un cluster: \(cluster(x)\).
- **Pérdida típica:** SSE (suma de distancias al centroide).
- **Parámetros:** centroides \(\{\mu_1, \dots, \mu_k\}\).
- **Optimización:** Algoritmo iterativo (K-means) o EM (Expectation-Maximization). No usan gradiente normalmente.

#### 6.4 Árboles de decisión
- **Pérdida:** Gini impurity o entropía.
  - \(Entropy = -\sum p_i \log p_i\)
- **Parámetros:** variables de split y umbrales (no continuos).
- **Optimización:** Algoritmo greedy que busca la mejor partición en cada nodo.

#### 6.5 Deep Learning
- **Modelo:** red neuronal profunda con millones de parámetros \(\theta\).
- **Pérdida:** según la tarea (MSE para regresión, cross-entropy para clasificación, focal loss para detección, etc.)
- **Optimización:** Gradiente descendiente con **backpropagation**. Optimizadores populares:
  - SGD (con o sin momentum)
  - Adam
  - RMSprop

---

### 7. Regularización

Para evitar overfitting, se añade un término de regularización a la función objetivo:

\[
L(\theta) = \text{Loss} + \lambda R(\theta)
\]

- \(R(\theta)\) puede ser la norma L2 (\(\|\theta\|^2\)) o L1 (\(\|\theta\|_1\)).
- \(\lambda\) controla la fuerza de la regularización.

**Ejemplo:** Regresión ridge: \(L = MSE + \lambda \|\theta\|^2\).

---

### 8. Parámetros y su Dimensionalidad

El número de parámetros varía enormemente:

| Modelo               | # parámetros aproximado |
|----------------------|-------------------------|
| Regresión lineal     | Pocos (número de features + 1) |
| Random Forest        | Miles (número de árboles y umbrales) |
| Red neuronal profunda| Millones (pesos de todas las conexiones) |

En general, \(\theta \in \mathbb{R}^d\) con \(d\) desde decenas hasta millones.

---

### 9. Resumen Conceptual

Todos los modelos de machine learning comparten la misma estructura:

| Paso | Concepto                |
|------|-------------------------|
| 1    | Modelo: \(f(x;\theta)\) |
| 2    | Pérdida individual: \(l(y, \hat{y})\) |
| 3    | Objetivo: \(L(\theta) = \frac{1}{n}\sum l(y_i, f(x_i;\theta))\) |
| 4    | Optimización: algoritmo que minimiza \(L(\theta)\) |

**Idea clave:** Toda rama de ML cambia solo estos tres elementos: el **modelo**, la **función de pérdida** y el **algoritmo de optimización**.

---

### 10. Optimizadores Más Usados en la Práctica

#### Machine Learning clásico
- **Closed form** (solución analítica, ej. regresión lineal)
- **Gradient Descent** (batch)
- **Coordinate Descent**
- **EM Algorithm** (para modelos con variables latentes, ej. clustering)

#### Deep Learning
- **SGD** (Stochastic Gradient Descent)
- **Adam** (Adaptive Moment Estimation) — el más dominante actualmente
- **AdamW** (Adam con decaimiento de peso corregido)
- **RMSprop**

---

### 11. Conclusión e Ideas Clave

- La **función de pérdida** define qué significa equivocarse para el problema en cuestión.
- El **optimizador** define cómo se corrigen los errores (cómo se actualizan los parámetros).
- La mayoría de los problemas de machine learning se pueden escribir como **minimización empírica del riesgo (ERM)**.
- La comprensión de estos fundamentos matemáticos es esencial para diseñar, implementar y depurar modelos de inteligencia artificial.


