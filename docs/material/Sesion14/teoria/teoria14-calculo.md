## Semana 14: Optimización y Gradiente Descendente

### Teoría

#### 1. Funciones cóncavas y convexas

- Una función \(f\) es **convexa** si el segmento que une dos puntos cualesquiera de su gráfica queda por encima de la gráfica. Formalmente, para todo \(x, y\) y \(\lambda \in [0,1]\):
  \[
  f(\lambda x + (1-\lambda) y) \leq \lambda f(x) + (1-\lambda) f(y)
  \]
- Una función es **cóncava** si \(-f\) es convexa (o si la desigualdad se invierte).

**Interpretación geométrica:** Las funciones convexas tienen forma de "U" (como \(x^2\)), las cóncavas tienen forma de "∩" (como \(\sqrt{x}\) o \(\ln x\)).

**Importancia en optimización:** Para funciones convexas, cualquier mínimo local es también mínimo global. Esto simplifica enormemente la búsqueda del óptimo.

**Ejemplo:** \(f(x) = x^2\) es convexa. \(f(x) = \ln x\) es cóncava en su dominio.

#### 2. Máximos y mínimos locales y globales

- **Mínimo local:** \(f(x^*)\) es menor que \(f(x)\) para todo \(x\) en un entorno de \(x^*\).
- **Mínimo global:** \(f(x^*)\) es el valor más pequeño de \(f\) en todo el dominio.
- Análogo para máximos.

**Ejemplo:** \(f(x) = x^3 - 3x\) tiene un máximo local en \(x=-1\) y un mínimo local en \(x=1\), pero no tiene mínimo global (tiende a \(-\infty\)).

#### 3. Problemas de optimización: minimización de funciones

En machine learning, casi todos los problemas se formulan como:

\[
\min_{\theta} L(\theta)
\]

donde \(L\) es una función de pérdida (o costo) y \(\theta\) son los parámetros del modelo. Buscamos el valor de \(\theta\) que hace mínima la pérdida.

#### 4. Descenso de gradiente: algoritmo e interpretación geométrica

El **descenso de gradiente** es un método iterativo para encontrar mínimos de una función diferenciable. La idea es moverse en la dirección opuesta al gradiente (dirección de máximo decrecimiento) para reducir el valor de la función.

**Algoritmo básico:**

1. Inicializar \(\theta\) aleatoriamente (o con algún valor).
2. Mientras no se alcance la convergencia:
   \[
   \theta \leftarrow \theta - \eta \nabla L(\theta)
   \]
   donde \(\eta > 0\) es la **tasa de aprendizaje** (learning rate).

**Interpretación geométrica:** El gradiente apunta en la dirección de máximo crecimiento. Por tanto, restarlo nos lleva cuesta abajo en la superficie de pérdida.

**Ejemplo unidimensional:** \(L(\theta) = \theta^2\). Gradiente: \(\nabla L = 2\theta\). Con \(\theta_0 = 3\), \(\eta = 0.1\):
- \(\theta_1 = 3 - 0.1 \times 6 = 2.4\)
- \(\theta_2 = 2.4 - 0.1 \times 4.8 = 1.92\)
- ... se aproxima a 0.

#### 5. Variantes del descenso de gradiente

- **SGD (Stochastic Gradient Descent):** En lugar de usar todo el dataset para calcular el gradiente, se usa un solo ejemplo (o un mini-batch). Es más rápido y puede escapar de mínimos locales. La actualización es:
  \[
  \theta \leftarrow \theta - \eta \nabla L_i(\theta)
  \]
  donde \(L_i\) es la pérdida para el ejemplo \(i\).

- **Momentum:** Acelera SGD acumulando una fracción del gradiente anterior. Ayuda a suavizar la trayectoria y a superar mesetas.
  \[
  v_t = \beta v_{t-1} + \eta \nabla L(\theta_t)
  \]
  \[
  \theta_{t+1} = \theta_t - v_t
  \]
  (con \(\beta\) típicamente 0.9).

- **RMSprop:** Adapta la tasa de aprendizaje dividiendo por la media cuadrática de los gradientes recientes.
  \[
  s_t = \beta s_{t-1} + (1-\beta) (\nabla L_t)^2
  \]
  \[
  \theta_{t+1} = \theta_t - \frac{\eta}{\sqrt{s_t + \epsilon}} \nabla L_t
  \]

- **Adam (Adaptive Moment Estimation):** Combina Momentum y RMSprop. Mantiene medias móviles del gradiente (primero momento) y del cuadrado del gradiente (segundo momento).
  \[
  m_t = \beta_1 m_{t-1} + (1-\beta_1) \nabla L_t
  \]
  \[
  v_t = \beta_2 v_{t-1} + (1-\beta_2) (\nabla L_t)^2
  \]
  \[
  \hat{m}_t = \frac{m_t}{1-\beta_1^t}, \quad \hat{v}_t = \frac{v_t}{1-\beta_2^t}
  \]
  \[
  \theta_{t+1} = \theta_t - \eta \frac{\hat{m}_t}{\sqrt{\hat{v}_t} + \epsilon}
  \]

#### 6. Programación de la tasa de aprendizaje (learning rate schedules)

- **Step decay:** Reducir la tasa de aprendizaje en un factor cada cierto número de épocas. Por ejemplo, multiplicar por 0.1 cada 30 épocas.
- **Cosine annealing:** La tasa de aprendizaje varía según una función coseno, descendiendo suavemente desde un valor inicial hasta un valor mínimo y luego reiniciándose (en versiones con reinicio).
  \[
  \eta_t = \eta_{\min} + \frac{1}{2}(\eta_{\max} - \eta_{\min}) \left(1 + \cos\left(\frac{T_{\text{cur}}}{T_{\max}} \pi\right)\right)
  \]

#### 7. Regularización como penalización en la función objetivo

A menudo se añade un término de regularización para controlar la complejidad del modelo y evitar sobreajuste. La función objetivo se convierte en:

\[
L_{\text{total}}(\theta) = L_{\text{original}}(\theta) + \lambda R(\theta)
\]

- **Regularización L2 (Ridge):** \(R(\theta) = \|\theta\|_2^2 = \sum \theta_i^2\). Penaliza pesos grandes y tiende a distribuirlos uniformemente.
- **Regularización L1 (Lasso):** \(R(\theta) = \|\theta\|_1 = \sum |\theta_i|\). Tiende a producir soluciones dispersas (muchos pesos exactamente cero).

#### 8. Condiciones de optimalidad

- **Punto crítico:** \(\nabla L(\theta) = 0\) (gradiente nulo). Puede ser mínimo, máximo o punto de silla.
- **Para funciones convexas:** cualquier punto crítico es un mínimo global.
- **Condición de segundo orden:** Si la matriz hessiana es definida positiva en un punto crítico, es un mínimo local. Si es definida negativa, es un máximo local. Si tiene autovalores de ambos signos, es un punto de silla.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Descenso de gradiente en regresión y clasificación

- **Regresión lineal con MSE:** El gradiente tiene forma cerrada, pero se puede usar gradiente descendente para datasets grandes. La actualización es:
  \[
  \mathbf{w} \leftarrow \mathbf{w} - \eta \frac{2}{n} \sum_{i=1}^n (\mathbf{w}^T \mathbf{x}_i - y_i) \mathbf{x}_i
  \]
- **Regresión logística:** Similar, con el gradiente \(\frac{1}{n} \sum (\hat{y}_i - y_i) \mathbf{x}_i\).

**Ejemplo numérico (regresión lineal con SGD):** Supongamos un punto \((x, y) = (2, 3)\), \(\mathbf{w} = [0.5]\), \(b=0\) (omitimos sesgo). Con MSE, la pérdida para ese punto es \((3 - 0.5*2)^2 = (3-1)^2 = 4\). Gradiente: \(2*(3-1)*(-2) = -8\). Con \(\eta=0.1\), nuevo peso: \(0.5 - 0.1*(-8) = 0.5 + 0.8 = 1.3\). Así, el peso aumenta para reducir el error.

##### 2. Gradient boosting (optimización)

En gradient boosting, cada nuevo árbol se ajusta a los **residuos** (gradientes negativos) de la función de pérdida. Por ejemplo, para MSE, el residuo es \(y - \hat{y}\). Esto es esencialmente un paso de descenso de gradiente en el espacio de funciones.

##### 3. Búsqueda de hiperparámetros

La optimización de hiperparámetros (como \(\eta\), \(\lambda\), etc.) se puede hacer mediante búsqueda en cuadrícula, búsqueda aleatoria o métodos bayesianos. Aunque no es gradiente descendente sobre los hiperparámetros (porque no son diferenciables), a menudo se usa el concepto de optimización para encontrar la mejor configuración.

#### Deep Learning (DL)

##### 1. SGD en redes neuronales

El entrenamiento de redes profundas casi siempre usa alguna variante de SGD. Por ejemplo, en PyTorch, `torch.optim.SGD` implementa SGD con o sin momentum.

##### 2. Momentum

Ayuda a acelerar el entrenamiento y a suavizar las oscilaciones. Especialmente útil en regiones donde el gradiente cambia de dirección.

##### 3. Adam y AdamW

- **Adam** es el optimizador por defecto en muchos problemas de DL. Combina las ventajas de Momentum y RMSprop.
- **AdamW** es una corrección de Adam que desacopla la regularización weight decay de la actualización adaptativa, mejorando la generalización.

##### 4. Cosine annealing

Se usa frecuentemente con reinicios (cosine annealing with restarts) para escapar de mínimos locales y explorar mejor el espacio de parámetros. Es común en entrenamiento de transformers y modelos de visión.

**Ejemplo:** En entrenamiento de ResNet en CIFAR-10, se puede programar la tasa de aprendizaje con cosine annealing de 0.1 a 0 durante 200 épocas.

##### 5. Optimización en agentes autónomos

En aprendizaje por refuerzo, los agentes se optimizan mediante algoritmos como policy gradient, que son esencialmente descenso de gradiente sobre la política. También se usan optimizadores como Adam para estabilizar el entrenamiento.

---

