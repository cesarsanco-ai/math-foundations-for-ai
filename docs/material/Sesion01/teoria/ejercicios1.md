## NOTACION BASICA

### Ejercicio 1: Cálculo del Error Cuadrático Medio (MSE)

El MSE es la función de costo más común en regresión. Se define mediante una **sumatoria**.

**Problema:** Dados los valores reales $y = [3, 5, 2]$ y las predicciones de tu modelo $\hat{y} = [2.5, 5, 3]$, calcula el error usando la fórmula:


$$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

**Paso a paso:**

1. **Identificar los índices:** Tenemos $n=3$ elementos. Los índices $i$ van de 1 a 3.
2. **Calcular las diferencias individuales ($y_i - \hat{y}_i$):**
* Para $i=1$: $(3 - 2.5) = 0.5$
* Para $i=2$: $(5 - 5) = 0$
* Para $i=3$: $(2 - 3) = -1$


3. **Elevar al cuadrado:**
* $0.5^2 = 0.25$
* $0^2 = 0$
* $(-1)^2 = 1$


4. **Aplicar la sumatoria ($\sum$):** $0.25 + 0 + 1 = 1.25$
5. **Dividir por $n$:** $MSE = 1.25 / 3 \approx 0.416$

---

### Ejercicio 2: Sumatoria Doble en una Matriz de Pesos

En redes neuronales, a veces necesitamos sumar todos los pesos de una capa (por ejemplo, para técnicas de regularización).

**Problema:** Dada la matriz de pesos $W$ de una capa que conecta 2 neuronas de entrada con 2 de salida:


$$W = \begin{pmatrix} w_{11} & w_{12} \\ w_{21} & w_{22} \end{pmatrix} = \begin{pmatrix} 0.2 & 0.5 \\ -0.1 & 0.8 \end{pmatrix}$$


Calcula la suma total de los pesos: $S = \sum_{i=1}^{2} \sum_{j=1}^{2} w_{ij}$

**Paso a paso:**

1. **Desglosar la sumatoria interna (fijando $i$):**
* Para $i=1$ (primera fila): $\sum_{j=1}^{2} w_{1j} = w_{11} + w_{12} = 0.2 + 0.5 = 0.7$
* Para $i=2$ (segunda fila): $\sum_{j=1}^{2} w_{2j} = w_{21} + w_{22} = -0.1 + 0.8 = 0.7$


2. **Sumar los resultados (sumatoria externa):**
* $S = 0.7 + 0.7 = 1.4$



---

### Ejercicio 3: Productoria de Probabilidades (Likelihood)

En modelos como "Naive Bayes", calculamos la probabilidad conjunta multiplicando probabilidades individuales.

**Problema:** Supongamos que la probabilidad de que tres palabras ($x_1, x_2, x_3$) aparezcan en un correo electrónico de "Spam" son $P(x_1)=0.1$, $P(x_2)=0.2$ y $P(x_3)=0.05$. Calcula la probabilidad total usando la **productoria**:


$$L = \prod_{i=1}^{3} P(x_i)$$

**Paso a paso:**

1. **Identificar los términos:** Tenemos 3 términos para multiplicar.
2. **Aplicar la operación ($\prod$):**
* $L = P(x_1) \cdot P(x_2) \cdot P(x_3)$
* $L = 0.1 \times 0.2 \times 0.05$


3. **Resultado final:**
* $0.1 \times 0.2 = 0.02$
* $0.02 \times 0.05 = 0.001$



## FUNCIONES BASICAS


### Ejercicio 1: Función Lineal (Predicción de Precios)

**Contexto:** Quieres predecir el precio de una vivienda basándote en su tamaño.
**Fórmula:** $f(x) = mx + b$

* $m = 50$ (precio por metro cuadrado en miles)
* $b = 20$ (costo base/fijo de servicios en miles)

**Problema:** Calcula el precio estimado para una casa de $x = 80$ metros cuadrados.

**Paso a paso:**

1. **Identificar variables:** $x=80$, $m=50$, $b=20$.
2. **Sustituir en la función:** $f(80) = 50(80) + 20$.
3. **Operar:** $4000 + 20 = 4020$.

* **Interpretación:** El precio estimado es de **4,020,000**.

---

### Ejercicio 2: Función Exponencial (Función Softmax)

**Contexto:** En clasificación multiclase, usamos la exponencial para resaltar el valor más alto (hacerlo "más positivo") antes de normalizar.
**Fórmula:** $f(x) = e^x$ (don tan $e \approx 2.718$)

**Problema:** Si la salida de una red neuronal para la clase "Gato" es $x = 2$, ¿cuál es su valor exponencial?

**Paso a paso:**

1. **Identificar base y exponente:** $e^{2}$.
2. **Calcular:** $2.718 \times 2.718 \approx 7.389$.

* **Uso en IA:** Este valor luego se divide por la suma de las exponenciales de todas las clases para obtener una probabilidad entre **0 y 1**.

---

### Ejercicio 3: Función Logarítmica (Log-Likelihood)

**Contexto:** Los logaritmos se usan para simplificar productos de probabilidades (como vimos en el ejercicio de productoria anterior) convirtiéndolos en sumas.
**Fórmula:** $f(x) = \ln(x)$ (Logaritmo natural)

**Problema:** Si la probabilidad conjunta de un modelo es $P = 0.001$, calcula el logaritmo de esa probabilidad.

**Paso a paso:**

1. **Sustituir:** $\ln(0.001)$.
2. **Calcular:** $\ln(10^{-3}) = -3 \cdot \ln(10) \approx -6.90$.

* **Uso en IA:** Es más fácil para una computadora optimizar $-6.90$ que manejar números decimales extremadamente pequeños (evita el error de *underflow*).

---

### Ejercicio 4: Función Sigmoide (Combinada)

Esta función es la "reina" de la Regresión Logística y las Redes Neuronales.
**Fórmula:** $\sigma(x) = \frac{1}{1 + e^{-x}}$

**Problema:** Si el resultado de tu combinación lineal $mx+b$ es $x = 0$, ¿cuál es la probabilidad resultante?

**Paso a paso:**

1. **Sustituir $x$:** $\frac{1}{1 + e^{0}}$.
2. **Recordar propiedad:** Cualquier número elevado a 0 es 1 ($e^0 = 1$).
3. **Calcular:** $\frac{1}{1 + 1} = \frac{1}{2} = 0.5$.

* **Interpretación:** Un valor de $0$ en la entrada de una sigmoide representa el umbral de decisión (50% de probabilidad).

---

## FUNCIONES DE ACTIVACION

---

### Ejercicio 1: La Función Sigmoide (Cálculo de Probabilidad)

**Contexto:** Tienes una red que clasifica si un cliente cancelará una suscripción (*churn*). La última capa (antes de la activación) devuelve un valor de $z = -1.5$.

**Problema:** Calcula la probabilidad final usando $\sigma(z) = \frac{1}{1+e^{-z}}$.

**Paso a paso:**

1. **Identificar la variable:** $z = -1.5$.
2. **Sustituir en la fórmula:** $\sigma(-1.5) = \frac{1}{1 + e^{-(-1.5)}} = \frac{1}{1 + e^{1.5}}$.
3. **Calcular el exponente:** $e^{1.5} \approx 4.481$.
4. **Resolver la fracción:** $\frac{1}{1 + 4.481} = \frac{1}{5.481} \approx 0.182$.

* **Conclusión:** Hay un **18.2%** de probabilidad de que el cliente cancele.

---

### Ejercicio 2: Tanh (Tangente Hiperbólica)

**Contexto:** La función Tanh es preferida en algunas capas ocultas porque sus salidas están centradas en cero (promedio cercano a 0), lo que ayuda a que el entrenamiento converja más rápido que con la sigmoide.

**Problema:** Calcula la activación para un valor de entrada $x = 0.5$.

**Paso a paso:**

1. **Fórmula:** $\tanh(0.5) = \frac{e^{0.5} - e^{-0.5}}{e^{0.5} + e^{-0.5}}$.
2. **Calcular exponenciales:**
* $e^{0.5} \approx 1.648$
* $e^{-0.5} \approx 0.606$


3. **Sustituir:** $\frac{1.648 - 0.606}{1.648 + 0.606} = \frac{1.042}{2.254} \approx 0.462$.

* **Nota:** Nota cómo una entrada positiva pequeña genera una salida positiva moderada dentro del rango $(-1, 1)$.

---

### Ejercicio 3: ReLU (Rectified Linear Unit)

**Contexto:** Es la función estándar para capas ocultas. Es extremadamente eficiente computacionalmente: solo es un umbral.

**Problema:** Calcula la salida de una neurona ReLU para dos posibles entradas: $x_1 = 4.2$ y $x_2 = -2.7$.

**Paso a paso para $x_1$:**

1. **Aplicar $f(x) = \max(0, x)$:** $\max(0, 4.2)$.
2. **Resultado:** $4.2$ (la función deja pasar el valor tal cual porque es positivo).

**Paso a paso para $x_2$:**

1. **Aplicar $f(x) = \max(0, x)$:** $\max(0, -2.7)$.
2. **Resultado:** $0$ (la neurona "muere" o se desactiva para valores negativos).

---

### Comparativa de Gradientes (Concepto para tus clases)


| Función | Derivada (Gradiente) en $x=10$ | Problema principal |
| --- | --- | --- |
| **Sigmoide** | Casi 0 (Saturación) | Desvanecimiento del gradiente (*Vanishing Gradient*). |
| **Tanh** | Casi 0 (Saturación) | Similar a la sigmoide, aunque un poco mejor. |
| **ReLU** | 1 (Constante) | Permite que el gradiente fluya sin disminuir en la zona positiva. |

---

## APLICACIONES EN IA



### Ejercicio 1: Regresión - Comparando MSE vs. MAE

**Contexto:** Estás entrenando un modelo para predecir el precio de acciones. Tienes un dato real $y = 100$ y tu modelo predijo $\hat{y} = 110$.

**Problema:** Calcula la pérdida usando MSE y MAE para entender cómo castigan el error.

**Paso a paso:**

1. **Calcular el error simple:** $e = y - \hat{y} = 100 - 110 = -10$.
2. **Cálculo de MAE (Error Absoluto):**
* $|-10| = 10$.


3. **Cálculo de MSE (Error Cuadrático):**
* $(-10)^2 = 100$.



> **Lección:** El MSE "amplifica" los errores grandes (los eleva al cuadrado), lo que hace que el modelo sea muy sensible a los valores atípicos (*outliers*), mientras que el MAE es más robusto.

---

### Ejercicio 2: Clasificación - Entropía Cruzada Binaria (Log Loss)

**Contexto:** Clasificas si una imagen es un "Gato" ($y=1$) o "No Gato" ($y=0$). Para una imagen que **sí es un gato**, tu modelo devuelve una probabilidad $p = 0.8$.

**Problema:** Calcula la pérdida de Entropía Cruzada: $L = -(y \log(p) + (1-y) \log(1-p))$.

**Paso a paso:**

1. **Identificar valores:** $y = 1$, $p = 0.8$.
2. **Sustituir en la fórmula:**
* $L = -[1 \cdot \log(0.8) + (1 - 1) \cdot \log(1 - 0.8)]$
* $L = -[1 \cdot \log(0.8) + 0 \cdot \log(0.2)]$


3. **Calcular:**
* $\log(0.8) \approx -0.223$
* $L = -(-0.223) = 0.223$



> **¿Qué pasa si el modelo falla?** Si predijera $p=0.1$ para un gato real, $L = -\log(0.1) \approx 2.3$. ¡La pérdida sube drásticamente!

---

### Ejercicio 3: Clustering - Compactación (Inercia/SSE)

**Contexto:** En K-Means, queremos que los puntos estén cerca de su centroide $\mu$.
**Problema:** Tienes un cluster con centroide $\mu = (2, 2)$ y un punto $x = (5, 6)$. Calcula la contribución de este punto al SSE (Suma de Errores al Cuadrado).

**Paso a paso:**

1. **Calcular la distancia vectorial ($x - \mu$):**
* $(5-2, 6-2) = (3, 4)$.


2. **Calcular la norma al cuadrado ($\|x - \mu\|^2$):**
* Usamos Pitágoras: $3^2 + 4^2 = 9 + 16 = 25$.


3. **Resultado:** El punto aporta **25** unidades a la "inercia" total del cluster.

---

### Ejercicio 4: Margen - Hinge Loss (SVM)

**Contexto:** Las Máquinas de Soporte Vectorial no solo quieren clasificar bien, quieren un "margen de seguridad".
**Fórmula:** $L = \max(0, 1 - y \cdot \hat{y})$, donde $y$ es la etiqueta real $\{-1, 1\}$.

**Problema:** Si la etiqueta es $y = 1$ y la salida del modelo es $\hat{y} = 0.7$ (clasificación correcta pero muy cerca del borde).

**Paso a paso:**

1. **Calcular el margen:** $y \cdot \hat{y} = 1 \cdot 0.7 = 0.7$.
2. **Evaluar la función:** $\max(0, 1 - 0.7) = \max(0, 0.3) = 0.3$.
3. **Interpretación:** Aunque el modelo acertó el signo, recibe una penalización de **0.3** porque no tuvo suficiente confianza (el margen ideal es $\ge 1$).

---

### Resumen para Aplicación en Modelado

| Objetivo | Función Sugerida | Comportamiento Clave |
| --- | --- | --- |
| **Predecir valores exactos** | MSE | Penaliza fuertemente errores grandes. |
| **Predecir probabilidades** | Cross-Entropy | Penaliza infinitamente si el modelo está 100% seguro y se equivoca. |
| **Separar clases con margen** | Hinge Loss | Ignora errores si la confianza es mayor a 1. |
| **Agrupar datos similares** | SSE | Minimiza la varianza interna de los grupos. |

## ESTRUCTURA GENERAL DE ML

Partiremos de la expresión más abstracta (ERM) y la iremos "aterrizando" hasta un cálculo numérico simple.

---

### 1. La Fórmula Maestra: Minimización del Riesgo Empírico (ERM)

Casi todo en IA se resume en esta expresión general:

$$\min_{\theta} \underbrace{\left[ \frac{1}{n} \sum_{i=1}^{n} l\big(y_i, f(x_i; \theta)\big) + \lambda R(\theta) \right]}_{L(\theta)}$$

**¿Qué significa cada pieza?**

1. **$\min_{\theta}$**: El objetivo. Buscamos los parámetros $\theta$ que hagan que todo lo de la derecha sea lo más pequeño posible.
2. **$\frac{1}{n} \sum l(\dots)$**: El **Costo**. Es el promedio de los errores individuales. Queremos que el modelo se ajuste a los datos actuales.
3. **$\lambda R(\theta)$**: La **Regularización**. Es una penalización por tener parámetros demasiado grandes o complejos. Queremos que el modelo sea simple para que funcione con datos nuevos (evitar *overfitting*).

---

### 2. Bajando al caso específico: Regresión Lineal con Penalización (Ridge)

Para aterrizar la fórmula anterior a un caso concreto, definimos qué funciones usaremos para cada pieza:

* **El Modelo $f$**: Una línea simple $\to f(x) = w \cdot x$ (donde $\theta = w$).
* **La Pérdida $l$**: Error al cuadrado $\to (y - \hat{y})^2$.
* **La Regularización $R$**: Penalización L2 $\to w^2$.

**La fórmula específica queda así:**


$$L(w) = \frac{1}{n} \sum (y_i - w x_i)^2 + \lambda w^2$$

---

### 3. Caso Práctico: Un "Dataset" de un solo punto

Para que el paso a paso sea claro, usemos un solo dato ($n=1$).

**Datos:**

* Entrada ($x$): $2$
* Salida real ($y$): $5$
* Parámetro actual ($w$): $3$ (Nuestro modelo dice: $3 \times 2 = 6$)
* Fuerza de regularización ($\lambda$): $0.1$

#### Paso 1: Calcular la Predicción ($\hat{y}$)

$$\hat{y} = w \cdot x = 3 \cdot 2 = 6$$

#### Paso 2: Calcular la Pérdida Individual ($l$)

$$l = (y - \hat{y})^2 = (5 - 6)^2 = (-1)^2 = 1$$

#### Paso 3: Calcular el Costo Promedio

Como solo hay un dato ($n=1$):


$$Costo = \frac{1}{1} \cdot 1 = 1$$

#### Paso 4: Calcular la Regularización ($R$)

$$R = \lambda \cdot w^2 = 0.1 \cdot (3)^2 = 0.1 \cdot 9 = 0.9$$

#### Paso 5: Calcular la Función Objetivo Final ($L$)

$$L(w) = Costo + Regularización = 1 + 0.9 = 1.9$$

---

### 4. ¿Cómo se usa esto para detectar errores?

Si el optimizador (como el Gradiente Descendente) ve que $L = 1.9$, intentará cambiar el valor de $w$.

* Si baja $w$ a **2.5**:
* $\hat{y} = 5$ (¡Predicción perfecta!), por lo que el Costo sería $0$.
* Regularización $= 0.1 \cdot (2.5)^2 = 0.625$.
* **Objetivo final $L = 0.625$**.


* **Detección:** Como $0.625 < 1.9$, el algoritmo sabe que $w=2.5$ es un "mejor" parámetro que $w=3$.

---

### Resumen

| Nivel | Representación | Ejemplo |
| --- | --- | --- |
| **General (ERM)** | $\min \frac{1}{n}\sum l + \lambda R$ | Teoría pura de Optimización. |
| **Algoritmo** | $\text{MSE} + \text{L2}$ | Regresión Ridge. |
| **Implementación** | `(y - w*x)**2 + 0.1*w**2` | Código en Python/NumPy. |
| **Instancia** | `(5 - 6)**2 + 0.9 = 1.9` | Un paso de entrenamiento específico. |


## CASOS ESPECIFICOS POR TIPO DE MODELO


### Ejercicio 1: El Corazón del ML (Estructura ERM)

**Pregunta:** Un modelo de Regresión Lineal tiene la función de costo $J(w) = \frac{1}{n} \sum (y_i - w x_i)^2 + \lambda w^2$. Si tenemos un solo dato $(x=1, y=4)$, un peso actual $w=2$ y una regularización $\lambda=0.5$, ¿cuál es el valor de la función objetivo?

**Respuesta Paso a Paso:**

1. **Predicción ($\hat{y}$):** $f(x) = w \cdot x \to 2 \cdot 1 = 2$.
2. **Pérdida Individual ($l$):** $(y - \hat{y})^2 \to (4 - 2)^2 = 2^2 = 4$.
3. **Costo ($J$):** Como $n=1$, el costo es simplemente la pérdida: $4$.
4. **Regularización ($R$):** $\lambda \cdot w^2 \to 0.5 \cdot (2)^2 = 0.5 \cdot 4 = 2$.
5. **Objetivo Final:** $Costo + Regularización = 4 + 2 = 6$.

---

### Ejercicio 2: Clasificación y Probabilidad (Sigmoide)

**Pregunta:** En un modelo de clasificación binaria, la salida de la combinación lineal es $z = 0$. ¿Cuál es la probabilidad predicha $p$ y cuál sería la pérdida de Entropía Cruzada si la etiqueta real es $y=1$?

**Respuesta Paso a Paso:**

1. **Calcular Probabilidad ($p$):** Aplicamos la sigmoide $\sigma(0) = \frac{1}{1 + e^{-0}} = \frac{1}{1 + 1} = 0.5$.
2. **Fórmula de Pérdida ($L$):** $L = -[y \log(p) + (1-y) \log(1-p)]$.
3. **Sustituir Valores:** $L = -[1 \cdot \log(0.5) + (1-1) \cdot \log(0.5)] = -\log(0.5)$.
4. **Resultado:** $\log(0.5) \approx -0.693$, por lo que $L \approx 0.693$.

---

### Ejercicio 3: Optimización (Gradient Descent)

**Pregunta:** Tienes un parámetro $w=5$ y el gradiente de la función de pérdida en ese punto es $\frac{\partial L}{\partial w} = 10$. Si usas una tasa de aprendizaje (learning rate) $\eta = 0.1$, ¿cuál será el nuevo valor de $w$?

**Respuesta Paso a Paso:**

1. **Fórmula de actualización:** $w_{nuevo} = w_{viejo} - \eta \cdot \text{Gradiente}$.
2. **Sustituir:** $w_{nuevo} = 5 - (0.1 \cdot 10)$.
3. **Calcular:** $5 - 1 = 4$.
4. **Interpretación:** Como el gradiente era positivo (la curva subía), el algoritmo restó valor a $w$ para "bajar" hacia el mínimo de la función.

---

### Ejercicio 4: Clustering (K-Means)

**Pregunta:** Un punto de datos está en las coordenadas $(3, 4)$. Hay dos centroides: $\mu_1 = (0, 0)$ y $\mu_2 = (5, 5)$. ¿A qué cluster se asigna el punto y por qué?

**Respuesta Paso a Paso:**

1. **Distancia a $\mu_1$:** $\sqrt{(3-0)^2 + (4-0)^2} = \sqrt{9 + 16} = 5$.
2. **Distancia a $\mu_2$:** $\sqrt{(3-5)^2 + (4-5)^2} = \sqrt{(-2)^2 + (-1)^2} = \sqrt{4 + 1} = \sqrt{5} \approx 2.23$.
3. **Decisión:** Se asigna al **Cluster 2** porque la distancia al centroide $\mu_2$ es menor ($2.23 < 5$).

---

### Ejercicio 5: Árboles de Decisión (Entropía)

**Pregunta:** Un conjunto de datos tiene 4 ejemplos: 2 de clase "A" y 2 de clase "B". ¿Cuál es la entropía de este conjunto?

**Respuesta Paso a Paso:**

1. **Calcular Probabilidades ($p_i$):** $p_A = 2/4 = 0.5$ y $p_B = 2/4 = 0.5$.
2. **Fórmula de Entropía:** $H = -(p_A \log_2 p_A + p_B \log_2 p_B)$.
3. **Sustituir:** $H = -(0.5 \cdot -1 + 0.5 \cdot -1) = -(-0.5 - 0.5) = 1$.
4. **Interpretación:** Una entropía de 1 significa desorden máximo (están mezclados 50/50).

---

## REGULARIZACION



### Ejercicio 1: Comparación L1 (Lasso) vs L2 (Ridge)

**Pregunta:** Tienes un modelo con dos pesos: $w_1 = 3$ y $w_2 = 4$. Si aplicamos una fuerza de regularización $\lambda = 0.1$, ¿cuál es la penalización total bajo la norma L1 y bajo la norma L2?

**Respuesta Paso a Paso:**

1. **Identificar los términos:** $w = [3, 4]$, $\lambda = 0.1$.
2. **Cálculo L2 (Ridge) - $R(\theta) = \sum w_i^2$:**
* Suma de cuadrados: $3^2 + 4^2 = 9 + 16 = 25$.
* Multiplicar por $\lambda$: $0.1 \cdot 25 = 2.5$.
* **Resultado L2:** La función objetivo sube en **2.5**.


3. **Cálculo L1 (Lasso) - $R(\theta) = \sum |w_i|$:**
* Suma de absolutos: $|3| + |4| = 7$.
* Multiplicar por $\lambda$: $0.1 \cdot 7 = 0.7$.
* **Resultado L1:** La función objetivo sube en **0.7**.



> **Interpretación para clase:** Nota cómo L2 penaliza mucho más fuerte a los valores grandes (al elevarlos al cuadrado), mientras que L1 es más "lineal".

---

### Ejercicio 2: El efecto del hiperparámetro $\lambda$

**Pregunta:** Supongamos que tu costo de entrenamiento (MSE) es **1.0** con un peso $w=10$.
Si $\lambda = 0$ y luego cambias a $\lambda = 0.5$, ¿qué le ocurre a la función objetivo $L$ bajo L2 y qué acción tomaría el optimizador?

**Respuesta Paso a Paso:**

1. **Caso $\lambda = 0$ (Sin regularización):**
* $L = 1.0 + (0 \cdot 10^2) = 1.0$.
* *Acción:* Al modelo no le importa que $w$ sea 10, solo le importa el error.


2. **Caso $\lambda = 0.5$ (Regularización fuerte):**
* $L = 1.0 + (0.5 \cdot 10^2) = 1.0 + 50 = 51.0$.
* *Acción:* ¡El objetivo saltó de 1 a 51!


3. **Acción del optimizador:**
* Para reducir ese 51, el optimizador (Gradiente Descendente) se verá forzado a **reducir drásticamente el valor de $w$**, incluso si eso hace que el MSE suba un poco (por ejemplo, de 1.0 a 1.2).
* **Resultado:** El modelo prefiere ser un poco menos preciso en el entrenamiento para ser mucho más simple (pesos más pequeños).



---

### Ejercicio 3: Detección de Overfitting

**Pregunta:** Estás entrenando un modelo y observas lo siguiente:

* Error Entrenamiento: 0.05
* Error Validación: 0.40
* Norma de los pesos $\|\theta\|^2$: 150.0

¿Cómo ayuda la fórmula $L = \text{Loss} + \lambda R(\theta)$ a solucionar este caso?

**Respuesta Paso a Paso:**

1. **Diagnóstico:** El error de entrenamiento es muy bajo pero el de validación es alto. Esto es **Overfitting**. Los pesos son muy grandes (150.0), lo que indica que el modelo está "memorizando" el ruido.
2. **Aplicación de la fórmula:** Al aumentar $\lambda$ (por ejemplo de 0.01 a 0.1), el término $\lambda R(\theta)$ se vuelve dominante en la función objetivo.
3. **Efecto:** El optimizador ya no puede mantener esos pesos de 150.0 porque inflan demasiado el valor de $L$.
4. **Corrección:** Los pesos bajan, el error de entrenamiento subirá un poco (ej. a 0.10), pero el error de validación bajará (ej. a 0.20) al ganar capacidad de generalización.

---

### Resumen de Conceptos Clave para Evaluación

| Tipo | Fórmula $R(\theta)$ | Efecto Principal | ¿Cuándo usarlo? |
| --- | --- | --- | --- |
| **L1 (Lasso)** | $\sum | w_i | $ |
| **L2 (Ridge)** | $\sum w_i^2$ | Distribuye el error entre pesos **pequeños**. | Casi siempre, para estabilidad numérica. |
| **Elastic Net** | $L1 + L2$ | Combinación de ambos. | En problemas complejos de alta dimensionalidad. |

## DIMENSIONALIDAD

---

### Ejercicio 1: Dimensionalidad en Modelos Lineales

**Pregunta:** Estás trabajando con un dataset para predecir el precio de casas que tiene 10 características (*features*), como metros cuadrados, número de habitaciones, etc. Si usas una **Regresión Lineal**, ¿cuál es la dimensionalidad del vector de parámetros $\theta$?

**Respuesta Paso a Paso:**

1. **Identificar la fórmula del modelo:** $\hat{y} = w_1x_1 + w_2x_2 + \dots + w_{10}x_{10} + b$.
2. **Contar los pesos ($w$):** Hay un peso por cada característica, es decir, 10 pesos.
3. **Contar el sesgo ($b$ o intercepto):** Siempre hay 1 término de sesgo (el "+1").
4. **Resultado:** $\theta \in \mathbb{R}^{11}$. La dimensionalidad $d$ es **11**.

---

### Ejercicio 2: El Salto a las Redes Neuronales (MLP)

**Pregunta:** Tienes una red neuronal muy pequeña con:

* Una capa de entrada de **5 neuronas**.
* Una única capa oculta de **10 neuronas**.
* Una capa de salida de **1 neurona**.
¿Cuántos parámetros $\theta$ tiene este modelo (considerando pesos y sesgos)?

**Respuesta Paso a Paso:**

1. **Conexión Entrada $\to$ Oculta:** Cada neurona de entrada se conecta con todas las ocultas.
* Pesos: $5 \times 10 = 50$.
* Sesgos: 10 (uno por cada neurona de la capa oculta).


2. **Conexión Oculta $\to$ Salida:**
* Pesos: $10 \times 1 = 10$.
* Sesgos: 1 (uno por la neurona de salida).


3. **Total:** $(50 + 10) + (10 + 1) = 60 + 11 = 71$.
4. **Resultado:** $\theta \in \mathbb{R}^{71}$.

> **Reflexión para clase:** Nota cómo con solo 5 entradas, una red pequeñísima ya tiene casi 7 veces más parámetros que una regresión lineal.

---

### Ejercicio 3: Relación entre Parámetros y Regularización

**Pregunta:** Si tienes un modelo donde la dimensionalidad de $\theta$ es muy alta ($d=1,000,000$) pero solo tienes $1,000$ ejemplos de entrenamiento ($n$), ¿qué parte de la fórmula general $L(\theta) = \text{Loss} + \lambda R(\theta)$ se vuelve crítica y por qué?

**Respuesta Paso a Paso:**

1. **Detección del problema:** Cuando $d \gg n$ (muchos más parámetros que datos), el modelo tiene demasiada "libertad" y puede memorizar los datos perfectamente. Esto es **overfitting** extremo.
2. **Análisis de la fórmula:** El término de **Loss** llegará a 0 fácilmente, pero el modelo no servirá para datos nuevos.
3. **Solución:** El término de **Regularización ($\lambda R(\theta)$)** se vuelve crítico.
4. **Acción:** Debemos usar un $\lambda$ alto para "restringir" esos millones de parámetros y obligar al modelo a quedarse solo con lo más importante.

---

### Cuadro Comparativo de Espacios de Parámetros

| Modelo | Espacio $\theta$ | Complejidad del Paisaje de Pérdida |
| --- | --- | --- |
| **Regresión Lineal** | $\mathbb{R}^{d+1}$ | **Convexo:** Solo un pozo, fácil de optimizar. |
| **Árboles (RF)** | No continuo | **Discreto:** No se puede usar gradiente, se busca por fuerza bruta. |
| **Deep Learning** | $\mathbb{R}^{millones}$ | **No Convexo:** Lleno de valles y picos, requiere optimizadores avanzados como Adam. |

### Resumen

"A mayor dimensionalidad de $\theta$, mayor es la capacidad del modelo para aprender, pero también es mayor el riesgo de que aprenda ruido. La **regularización** es el freno de mano que evita que un modelo de millones de parámetros se descontrole."


## CONCEPTOS

No importa si es un LLM moderno o una regresión de hace 50 años; solo se tiene que identificar estos 4 pasos, para entender el modelo.

---

### Ejercicio 1: Identificación de Componentes (El "Template")

**Pregunta:** Un colega te presenta un nuevo algoritmo para detectar fraude bancario. Te dice: *"Usamos una **Red Neuronal**, comparamos la probabilidad con la etiqueta real usando **Cross-Entropy** y ajustamos los pesos con **Adam**"*.

Completa la tabla del resumen conceptual para este nuevo algoritmo:

**Respuesta Paso a Paso:**

| Paso | Concepto | Caso: Detección de Fraude |
| --- | --- | --- |
| **1** | **Modelo** $f(x;\theta)$ | Red Neuronal (millones de parámetros $\theta$) |
| **2** | **Pérdida** $l(y, \hat{y})$ | Cross-Entropy (Entropía Cruzada) |
| **3** | **Objetivo** $L(\theta)$ | Promedio de Cross-Entropy en el dataset de transacciones |
| **4** | **Optimización** | Algoritmo **Adam** (basado en gradiente) |

---

### Ejercicio 2: El Cambio de Paradigma (De Regresión a Clustering)

**Pregunta:** Tienes un modelo de **Regresión Lineal** (MSE + Gradiente Descendente). Si decides cambiar el problema a uno de **Clustering (K-Means)** para agrupar clientes, ¿qué elementos de la tabla cambian?

**Respuesta Paso a Paso:**

1. **Cambio en el Modelo ($f$):** Pasas de una línea $w \cdot x + b$ a una función que asigna puntos al **centroide** $\mu$ más cercano.
2. **Cambio en la Pérdida ($l$):** Pasas de la diferencia al cuadrado $(y - \hat{y})^2$ a la **distancia euclidiana** entre el punto y su centroide $\|x - \mu\|^2$.
3. **Cambio en la Optimización:** Pasas de seguir la pendiente (Gradiente) a un **proceso iterativo** de "Asignar y Recalcular promedios".

> **Conclusión:** El paso 3 (El Objetivo de minimizar un error) se mantiene, pero las herramientas dentro de cada paso cambian totalmente.

---

### Ejercicio 3: Diagnóstico de Modelos (¿Dónde está el problema?)

**Pregunta:** Un modelo de IA está funcionando muy mal. Los datos son correctos, pero las predicciones son erráticas. Como Data Scientist, debes revisar los 4 pasos. ¿Qué buscarías en cada uno?

**Respuesta Paso a Paso:**

* **¿Falla el Paso 1 (Modelo)?**: Quizás el modelo es demasiado simple (una línea para datos curvos). *Solución: Aumentar la complejidad o dimensionalidad de $\theta$.*
* **¿Falla el Paso 2 (Pérdida)?**: Quizás estás usando MSE para un problema de clasificación de imágenes. *Solución: Cambiar la función de pérdida a una adecuada (Cross-Entropy).*
* **¿Falla el Paso 4 (Optimización)?**: Quizás el algoritmo (Gradiente) se quedó atrapado o la tasa de aprendizaje es muy alta. *Solución: Cambiar a un optimizador más robusto como Adam o ajustar los hiperparámetros.*

---

### Resumen 

El ML es como una "fábrica" con piezas intercambiables:

| Pieza | Si es Regresión... | Si es Clasificación... | Si es Deep Learning... |
| --- | --- | --- | --- |
| **Modelo** | Recta / Plano | Sigmoide / Softmax | Capas Densas / Convoluciones |
| **Pérdida** | Distancia (MSE/MAE) | Probabilidad (Log-Loss) | Específica de la tarea |
| **Optimización** | Ecuaciones Normales / GD | SGD / L-BFGS | Backpropagation / Adam / RMSprop |

---
## OPTIMIZADORES

Analogia: El Modelo es el "vehículo" y la Pérdida es el "mapa", el **Optimizador** es el "conductor" que decide qué tan rápido y en qué dirección mover el volante.

---

### Ejercicio 1: Solución Analítica (Closed Form)

**Pregunta:** Tienes un dataset pequeñito de Regresión Lineal y decides no usar Gradiente Descendente, sino resolverlo de un solo golpe con la **Ecuación Normal**: $\theta = (X^T X)^{-1} X^T y$. Si el cálculo de $(X^T X)^{-1}$ es posible, ¿por qué un Data Scientist preferiría usar Gradiente Descendente en lugar de esta solución exacta?

**Respuesta Paso a Paso:**

1. **Analizar la complejidad:** Invertir una matriz tiene una complejidad de aproximadamente $O(d^3)$, donde $d$ es el número de características (features).
2. **Caso Real:** Si tienes un modelo con $d = 100,000$ características:
* La inversión de matriz requeriría una potencia de cómputo y memoria RAM inmensa.


3. **Comparación:** El **Gradient Descent** es iterativo y solo requiere multiplicar matrices ($O(d^2)$), lo cual es mucho más eficiente para Big Data.
4. **Conclusión:** Se prefiere el Gradiente cuando el dataset es demasiado grande para caber en la memoria o cuando el modelo no es lineal.

---

### Ejercicio 2: El poder de Adam (Adaptive Moment Estimation)

**Pregunta:** ¿Cuál es la diferencia fundamental entre un **SGD simple** y **Adam**, y por qué Adam es el "estándar de oro" en Deep Learning hoy en día?

**Respuesta Paso a Paso:**

1. **SGD Simple:** Usa una única tasa de aprendizaje ($\eta$) para todos los parámetros. Si un parámetro necesita cambios pequeños y otro cambios grandes, el SGD suele fallar o ser muy lento.
2. **Mecanismo de Adam:** * **Momento:** Recuerda la dirección de los pasos anteriores para no oscilar locamente.
* **Adaptatividad:** Calcula una tasa de aprendizaje individual para cada parámetro.


3. **Analogía:** El SGD es como bajar una montaña a ciegas dando pasos siempre del mismo tamaño; **Adam** es como tener un GPS que detecta si el suelo está resbaladizo o muy empinado y ajusta tu velocidad en cada pie.
4. **Resultado:** Adam converge mucho más rápido y es menos sensible a la elección inicial de la tasa de aprendizaje.

---

### Ejercicio 3: El algoritmo EM (Clustering)

**Pregunta:** En K-Means o Modelos de Mezcla Gaussiana, usamos el algoritmo **Expectation-Maximization (EM)**. ¿Por qué no usamos Gradiente Descendente aquí?

**Respuesta Paso a Paso:**

1. **Detectar la naturaleza del problema:** En clustering, la pérdida depende de a qué grupo pertenece cada punto (una variable "latente" u oculta).
2. **El problema del Gradiente:** La función de pertenencia es discreta (o eres del grupo 1 o del 2). Las funciones discretas no tienen derivadas suaves, por lo que el gradiente "no sabe hacia dónde ir".
3. **Lógica del EM:**
* **Paso E (Expectation):** Estima a qué grupo pertenece cada punto.
* **Paso M (Maximization):** Ajusta los parámetros del grupo (centroides) para minimizar la pérdida.


4. **Conclusión:** Es una optimización coordinada que salta entre asignar y ajustar, ideal para modelos donde no podemos derivar directamente.

---

### Tabla Comparativa de "Conductores" (Optimizadores)

| Escenario | Optimizador Sugerido | Razón Principal |
| --- | --- | --- |
| **Pocos datos, modelo lineal** | Solución Analítica | Es exacta y rápida en hardware modesto. |
| **Dataset gigante, modelo simple** | SGD | Muy eficiente en memoria (procesa de a pocos datos). |
| **Redes Neuronales Profundas** | **Adam / AdamW** | Robusto, rápido y maneja bien gradientes ruidosos. |
| **Agrupamiento (Clustering)** | EM Algorithm | Maneja variables que no podemos ver directamente. |

---

### TEST BREVE

Intenta responder esta pregunta integradora:

> *"Si un modelo de **Deep Learning** (millones de parámetros) tiene un error de entrenamiento casi en cero pero un error de validación muy alto, y estás usando **Adam** como optimizador... ¿Qué pieza de la fórmula $L(\theta) = \text{Loss} + \lambda R(\theta)$ deberías ajustar y por qué?"*

**Respuesta Pro:** Deberías aumentar la **Regularización ($\lambda R(\theta)$)**. Aunque Adam es un optimizador excelente (Paso 4), el problema es de **Overfitting** debido a la alta dimensionalidad (Paso 8). Adam está haciendo "demasiado bien" su trabajo de minimizar la Loss, y necesitas ponerle un freno matemático para que el modelo generalice.

