---
layout: default
---
# Sesión 12: Derivadas e Integrales en una Variable

### Teoría

#### 1. Derivada como tasa de cambio, interpretación geométrica

La **derivada** de una función $f(x)$ en un punto $x_0$ mide la tasa de cambio instantánea de la función en ese punto. Geométricamente, es la pendiente de la recta tangente a la curva $y = f(x)$ en el punto $(x_0, f(x_0))$.

**Definición formal:**
$$
f'(x_0) = \lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h}
$$
si este límite existe.

**Ejemplo paso a paso:** Sea $f(x) = x^2$. Calculemos $f'(2)$:
$$
f'(2) = \lim_{h \to 0} \frac{(2+h)^2 - 2^2}{h} = \lim_{h \to 0} \frac{4 + 4h + h^2 - 4}{h} = \lim_{h \to 0} \frac{4h + h^2}{h} = \lim_{h \to 0} (4 + h) = 4
$$
La pendiente de la tangente en $x=2$ es 4.

#### 2. Reglas de derivación

- **Regla del producto:** $(f \cdot g)' = f' g + f g'$
- **Regla del cociente:** $\left(\frac{f}{g}\right)' = \frac{f' g - f g'}{g^2}$
- **Regla de la cadena:** $(f \circ g)'(x) = f'(g(x)) \cdot g'(x)$

**Ejemplo regla del producto:** $h(x) = x^2 \sin x$.  
$h'(x) = (x^2)' \sin x + x^2 (\sin x)' = 2x \sin x + x^2 \cos x$.

**Ejemplo regla del cociente:** $h(x) = \frac{\ln x}{x}$.  
$h'(x) = \frac{(\ln x)' \cdot x - \ln x \cdot (x)'}{x^2} = \frac{\frac{1}{x} \cdot x - \ln x \cdot 1}{x^2} = \frac{1 - \ln x}{x^2}$.

**Ejemplo regla de la cadena:** $h(x) = \sin(x^2)$.  
$h'(x) = \cos(x^2) \cdot (x^2)' = \cos(x^2) \cdot 2x = 2x \cos(x^2)$.

#### 3. Derivación simple y de orden n

La derivada de orden $n$ (enésima derivada) se obtiene derivando sucesivamente $n$ veces. Se denota $f^{(n)}(x)$.

**Ejemplo:** $f(x) = x^4$.  
$f'(x) = 4x^3$, $f''(x) = 12x^2$, $f'''(x) = 24x$, $f^{(4)}(x) = 24$, $f^{(5)}(x) = 0$.

#### 4. Derivadas de funciones elementales

- **Polinomios:** $\frac{d}{dx} x^n = n x^{n-1}$
- **Exponencial:** $\frac{d}{dx} e^x = e^x$; $\frac{d}{dx} a^x = a^x \ln a$
- **Logaritmo:** $\frac{d}{dx} \ln x = \frac{1}{x}$; $\frac{d}{dx} \log_a x = \frac{1}{x \ln a}$
- **Seno:** $\frac{d}{dx} \sin x = \cos x$
- **Coseno:** $\frac{d}{dx} \cos x = -\sin x$
- **Sigmoide:** $\sigma(x) = \frac{1}{1 + e^{-x}}$. Su derivada es $\sigma'(x) = \sigma(x) (1 - \sigma(x))$. Veremos la deducción en aplicaciones.
- **Tanh:** $\tanh x = \frac{e^x - e^{-x}}{e^x + e^{-x}}$. Su derivada es $\tanh'(x) = 1 - \tanh^2 x$.

#### 5. Derivada de funciones compuestas

Aplicando la regla de la cadena repetidamente. Por ejemplo, $f(x) = \ln(\sin(e^x))$:
$$
f'(x) = \frac{1}{\sin(e^x)} \cdot \cos(e^x) \cdot e^x = \frac{e^x \cos(e^x)}{\sin(e^x)} = e^x \cot(e^x).
$$

#### 6. Integral definida como área bajo la curva

La **integral definida** de $f(x)$ desde $a$ hasta $b$ representa el área neta bajo la curva de $f$ entre esos límites (considerando áreas negativas cuando la función es negativa).

$$
\int_a^b f(x) \, dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^*) \Delta x
$$

**Teorema Fundamental del Cálculo:** Si $F$ es una primitiva de $f$ (es decir, $F' = f$), entonces
$$
\int_a^b f(x) \, dx = F(b) - F(a).
$$

**Ejemplo:** $\int_0^1 x^2 \, dx$. Una primitiva es $F(x) = \frac{x^3}{3}$. Entonces $\int_0^1 x^2 dx = \frac{1^3}{3} - \frac{0^3}{3} = \frac{1}{3}$.

#### 7. Aplicación: cálculo de áreas (AUC)

El área bajo la curva (Area Under the Curve) es una medida común en estadística y machine learning, especialmente para la curva ROC. Se calcula mediante integración numérica o analítica si se conoce la función.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Derivadas para gradiente en regresión en 1D

En regresión lineal simple con una variable, el modelo es $\hat{y} = wx + b$. La función de costo MSE es:
$$
L(w, b) = \frac{1}{n} \sum_{i=1}^n (y_i - (w x_i + b))^2
$$
Para minimizar, necesitamos las derivadas parciales respecto a $w$ y $b$. La derivada respecto a $w$ (considerando $b$ constante) es:
$$
\frac{\partial L}{\partial w} = \frac{1}{n} \sum_{i=1}^n 2(y_i - (w x_i + b)) \cdot (-x_i) = -\frac{2}{n} \sum_{i=1}^n x_i (y_i - \hat{y}_i)
$$
Análogamente para $b$. Estas derivadas se usan en el descenso de gradiente.

**Ejemplo numérico:** Con un solo punto $(x, y) = (2, 3)$ y parámetros actuales $w=0.5, b=0$, la predicción es $\hat{y}=1$. El error es $3-1=2$. La derivada parcial de $L$ (para un punto, sin promediar) respecto a $w$ es $-2 \cdot 2 \cdot 2 = -8$ (usando la fórmula sin el 1/n). Así, el gradiente indica que debemos aumentar $w$ para reducir el error.

##### 2. Derivada de la función sigmoide

La función sigmoide $\sigma(x) = \frac{1}{1+e^{-x}}$ es crucial en regresión logística y redes neuronales. Su derivada se obtiene aplicando reglas de derivación:

$$
\sigma'(x) = \frac{d}{dx} (1+e^{-x})^{-1} = -1 \cdot (1+e^{-x})^{-2} \cdot \frac{d}{dx}(1+e^{-x}) = -\frac{1}{(1+e^{-x})^2} \cdot (-e^{-x}) = \frac{e^{-x}}{(1+e^{-x})^2}
$$
Observamos que $e^{-x} = \frac{1-\sigma(x)}{\sigma(x)}$? En realidad, podemos expresarlo en términos de $\sigma$:
$$
\sigma'(x) = \sigma(x) (1 - \sigma(x))
$$
Verificación: $\sigma(x) = 1/(1+e^{-x})$, entonces $1-\sigma(x) = e^{-x}/(1+e^{-x})$. Multiplicando: $\sigma(x)(1-\sigma(x)) = \frac{1}{1+e^{-x}} \cdot \frac{e^{-x}}{1+e^{-x}} = \frac{e^{-x}}{(1+e^{-x})^2}$, que es justo lo obtenido.

Esta propiedad simplifica el cálculo en backpropagation, ya que la derivada depende solo de la salida de la neurona.

##### 3. Derivada de la log-loss (entropía cruzada binaria)

La función de pérdida para un ejemplo en clasificación binaria es:
$$
\ell(y, \hat{y}) = -[y \log \hat{y} + (1-y) \log(1-\hat{y})]
$$
donde $\hat{y} = \sigma(z)$ y $z = w^T x + b$. Para el gradiente respecto a $z$, aplicamos regla de la cadena:
$$
\frac{\partial \ell}{\partial z} = \frac{\partial \ell}{\partial \hat{y}} \cdot \frac{\partial \hat{y}}{\partial z} = \left( -\frac{y}{\hat{y}} + \frac{1-y}{1-\hat{y}} \right) \cdot \hat{y}(1-\hat{y}) = -y(1-\hat{y}) + (1-y)\hat{y} = \hat{y} - y
$$
Resultado elegante: el gradiente es simplemente la diferencia entre la predicción y la etiqueta.

##### 4. Gradiente en boosting

En gradient boosting, en cada iteración se ajusta un modelo débil a los **residuos** (gradientes negativos) de la función de pérdida. Para regresión con MSE, el residuo es $y - \hat{y}$ (que es el gradiente de MSE). Para clasificación con log-loss, el gradiente también es $\hat{y} - y$.

##### 5. AUC (Area Under the Curve)

El AUC de la curva ROC se calcula como la integral de la tasa de verdaderos positivos (TPR) en función de la tasa de falsos positivos (FPR). Matemáticamente:
$$
\text{AUC} = \int_0^1 \text{TPR}(t) \, d(\text{FPR}(t))
$$
En la práctica, se aproxima mediante sumas trapezoidales. Una interpretación probabilística: AUC es la probabilidad de que un clasificador asigne una puntuación más alta a un positivo aleatorio que a un negativo aleatorio.

##### 6. Integrales en probabilidades

En probabilidad, la función de distribución acumulada (CDF) es la integral de la densidad: $F(x) = \int_{-\infty}^x f(t) dt$. La esperanza de una variable continua es $E[X] = \int x f(x) dx$. Estas integrales aparecen en modelos probabilísticos y en métricas como el error esperado.

#### Deep Learning (DL)

##### 1. Derivadas en backpropagation (regla de la cadena)

El algoritmo de backpropagation es una aplicación sistemática de la regla de la cadena para calcular gradientes de la pérdida respecto a todos los parámetros de la red. Por ejemplo, en una red con una capa oculta:

- $z_1 = W_1 x + b_1$
- $a_1 = \sigma(z_1)$
- $z_2 = W_2 a_1 + b_2$
- $\hat{y} = \sigma(z_2)$
- $L = \ell(y, \hat{y})$

Para $\frac{\partial L}{\partial W_2}$, aplicamos:
$$
\frac{\partial L}{\partial W_2} = \frac{\partial L}{\partial \hat{y}} \cdot \frac{\partial \hat{y}}{\partial z_2} \cdot \frac{\partial z_2}{\partial W_2}
$$
Ya conocemos $\frac{\partial L}{\partial \hat{y}} = \hat{y} - y$ (para log-loss) y $\frac{\partial \hat{y}}{\partial z_2} = \hat{y}(1-\hat{y})$. Además, $\frac{\partial z_2}{\partial W_2} = a_1^T$ (en forma matricial). Así, el gradiente se propaga hacia atrás.

##### 2. Derivadas de funciones de activación

En backpropagation, necesitamos las derivadas de las activaciones:
- ReLU: $\frac{d}{dx} \max(0, x) = \begin{cases} 1 & x > 0 \\ \text{indefinido en 0 (se toma subgradiente 0 o 1)} \end{cases}$
- Tanh: $\frac{d}{dx} \tanh x = 1 - \tanh^2 x$
- Sigmoide: $\sigma'(x) = \sigma(x)(1-\sigma(x))$

##### 3. Pérdidas basadas en integrales (cross-entropy)

La entropía cruzada para clasificación multiclase es:
$$
L = -\sum_{k=1}^K y_k \log \hat{y}_k
$$
donde $\hat{y}_k = \frac{e^{z_k}}{\sum_j e^{z_j}}$ (softmax). La derivada respecto a $z_i$ es:
$$
\frac{\partial L}{\partial z_i} = \hat{y}_i - y_i
$$
(verificable mediante cálculo). Esta forma simple es consecuencia de la estructura de la función softmax y la log-verosimilitud.

---

