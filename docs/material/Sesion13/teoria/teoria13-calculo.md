## Semana 13: Cálculo Multivariable

### Teoría

#### 1. Funciones de varias variables, representación y visualización

Una **función de varias variables** asigna a cada punto \((x_1, x_2, \dots, x_n)\) en \(\mathbb{R}^n\) un valor real \(f(x_1, x_2, \dots, x_n)\). Se denota \(f: \mathbb{R}^n \to \mathbb{R}\).

**Ejemplos:**
- \(f(x, y) = x^2 + y^2\) (un paraboloide).
- \(f(x, y) = \sin(x) \cos(y)\).
- En ML, la función de pérdida \(L(\theta_1, \theta_2, \dots, \theta_p)\) depende de muchos parámetros.

**Representación y visualización:**
- Para \(n=2\), podemos graficar la superficie \(z = f(x, y)\) en 3D.
- También se usan curvas de nivel (contornos) para visualizar en 2D.

**Ejemplo:** \(f(x, y) = x^2 + y^2\). Sus curvas de nivel son círculos concéntricos.

#### 2. Derivadas parciales

La **derivada parcial** de \(f\) respecto a \(x_i\) mide la tasa de cambio de \(f\) cuando solo \(x_i\) varía, manteniendo las demás variables constantes. Se denota \(\frac{\partial f}{\partial x_i}\) o \(f_{x_i}\).

**Definición:**
\[
\frac{\partial f}{\partial x_i}(x_1, \dots, x_n) = \lim_{h \to 0} \frac{f(x_1, \dots, x_i + h, \dots, x_n) - f(x_1, \dots, x_n)}{h}
\]

**Ejemplo paso a paso:** Sea \(f(x, y) = x^2 y + \sin(xy)\).  
- Derivada parcial respecto a \(x\): tratamos \(y\) como constante.  
  \(\frac{\partial}{\partial x}(x^2 y) = 2x y\).  
  \(\frac{\partial}{\partial x} \sin(xy) = \cos(xy) \cdot y\) (por regla de la cadena).  
  Entonces \(\frac{\partial f}{\partial x} = 2xy + y \cos(xy)\).  
- Derivada parcial respecto a \(y\): tratamos \(x\) como constante.  
  \(\frac{\partial}{\partial y}(x^2 y) = x^2\).  
  \(\frac{\partial}{\partial y} \sin(xy) = \cos(xy) \cdot x\).  
  Entonces \(\frac{\partial f}{\partial y} = x^2 + x \cos(xy)\).

#### 3. Vector gradiente, interpretación geométrica (dirección de máximo crecimiento)

El **gradiente** de \(f\) en un punto es el vector formado por todas sus derivadas parciales:

\[
\nabla f(\mathbf{x}) = \begin{pmatrix} \frac{\partial f}{\partial x_1}, & \frac{\partial f}{\partial x_2}, & \dots, & \frac{\partial f}{\partial x_n} \end{pmatrix}^T
\]

**Propiedades geométricas:**
- El gradiente apunta en la dirección de **máximo crecimiento** (mayor incremento) de la función.
- Su magnitud \(|\nabla f|\) indica la tasa de crecimiento en esa dirección.
- El gradiente es perpendicular a las curvas (o superficies) de nivel.

**Ejemplo:** Para \(f(x, y) = x^2 + y^2\), el gradiente es \(\nabla f = (2x, 2y)\). En el punto \((1, 1)\), el gradiente es \((2, 2)\), que apunta hacia afuera del círculo de nivel, en dirección de máximo aumento de \(f\). Efectivamente, moviéndonos en esa dirección, \(f\) crece más rápido.

#### 4. Regla de la cadena multivariable

Si tenemos una función compuesta \(f(\mathbf{x}(t))\) donde \(\mathbf{x}(t)\) es una trayectoria, o más generalmente \(f(\mathbf{x})\) y \(\mathbf{x} = \mathbf{g}(\mathbf{u})\), la derivada se obtiene mediante:

\[
\frac{\partial f}{\partial u_j} = \sum_{i=1}^n \frac{\partial f}{\partial x_i} \frac{\partial x_i}{\partial u_j}
\]

En forma vectorial, si \(\mathbf{x} = \mathbf{g}(\mathbf{u})\), entonces la matriz jacobiana de la composición es el producto de las matrices jacobianas.

**Ejemplo:** \(f(x, y) = x^2 + y^2\), con \(x = u v\), \(y = u + v\). Calculemos \(\frac{\partial f}{\partial u}\):
\[
\frac{\partial f}{\partial u} = \frac{\partial f}{\partial x} \frac{\partial x}{\partial u} + \frac{\partial f}{\partial y} \frac{\partial y}{\partial u} = (2x)(v) + (2y)(1) = 2xv + 2y
\]
Sustituyendo \(x = uv, y = u+v\): \(\frac{\partial f}{\partial u} = 2(uv)v + 2(u+v) = 2uv^2 + 2u + 2v\).

#### 5. Matriz Jacobiana y Hessiana (introducción y significado)

- **Jacobiana:** Para una función vectorial \(\mathbf{f}: \mathbb{R}^n \to \mathbb{R}^m\), la matriz jacobiana \(J\) tiene dimensiones \(m \times n\) y su entrada \((i, j)\) es \(\frac{\partial f_i}{\partial x_j}\). En optimización, el gradiente es un caso particular (\(m=1\)).

- **Hessiana:** Para una función escalar \(f: \mathbb{R}^n \to \mathbb{R}\), la matriz hessiana \(H\) es de \(n \times n\) con entradas \(H_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}\). Es simétrica si las derivadas cruzadas son continuas.

**Significado:**
- La Hessiana contiene información sobre la **curvatura** de la función en todas las direcciones.
- Sus autovalores indican si un punto crítico es mínimo (todos positivos), máximo (todos negativos) o punto de silla (autovalores mixtos).
- En optimización, se usa en métodos de Newton y para analizar la convergencia.

**Ejemplo:** \(f(x, y) = x^2 + xy + y^2\).  
Gradiente: \(\nabla f = (2x + y, x + 2y)\).  
Hessiana:  
\(\frac{\partial^2 f}{\partial x^2} = 2\), \(\frac{\partial^2 f}{\partial y^2} = 2\), \(\frac{\partial^2 f}{\partial x \partial y} = 1\).  
Entonces \(H = \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}\). Sus autovalores son 3 y 1 (positivos), indicando que el punto crítico (0,0) es un mínimo.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Gradiente de funciones de costo con múltiples parámetros

En ML, la función de costo depende de muchos parámetros. Por ejemplo, en regresión lineal con \(p\) características, el costo MSE es:
\[
L(\mathbf{w}) = \frac{1}{n} \sum_{i=1}^n (y_i - \mathbf{w}^T \mathbf{x}_i)^2
\]
El gradiente respecto a \(\mathbf{w}\) es:
\[
\nabla L(\mathbf{w}) = -\frac{2}{n} \sum_{i=1}^n (y_i - \mathbf{w}^T \mathbf{x}_i) \mathbf{x}_i
\]
(que es un vector). Este gradiente se usa en el descenso de gradiente para actualizar todos los pesos simultáneamente.

**Ejemplo numérico con 2 parámetros:** Supongamos dos puntos: \((x_1, y_1) = (1, 2)\) y \((x_2, y_2) = (2, 3)\), modelo \(\hat{y} = w_1 x_1 + w_2 x_2\) (sin sesgo). Entonces:
\[
L(w_1, w_2) = \frac{1}{2}[(2 - (w_1\cdot1 + w_2\cdot1))^2 + (3 - (w_1\cdot2 + w_2\cdot2))^2]
\]
Simplificando: \(L = \frac{1}{2}[(2 - (w_1+w_2))^2 + (3 - 2(w_1+w_2))^2]\). Sea \(s = w_1+w_2\), entonces \(L(s) = \frac{1}{2}[(2-s)^2 + (3-2s)^2]\). Derivando respecto a \(s\): \(L'(s) = - (2-s) - 2(3-2s) = -2 + s -6 + 4s = 5s - 8\). Como \(\frac{\partial s}{\partial w_1} = 1\), \(\frac{\partial s}{\partial w_2} = 1\), entonces \(\frac{\partial L}{\partial w_1} = \frac{\partial L}{\partial s} \cdot 1 = 5s - 8\), igual para \(w_2\). Así, el gradiente es el mismo para ambos pesos, lo que tiene sentido por simetría.

##### 2. Gradiente de log-loss en regresión logística

En regresión logística, la función de costo (log-loss) para un conjunto de datos es:
\[
L(\mathbf{w}, b) = -\frac{1}{n} \sum_{i=1}^n [y_i \log \hat{y}_i + (1-y_i) \log(1-\hat{y}_i)]
\]
con \(\hat{y}_i = \sigma(\mathbf{w}^T \mathbf{x}_i + b)\). El gradiente respecto a \(\mathbf{w}\) es:
\[
\nabla_{\mathbf{w}} L = \frac{1}{n} \sum_{i=1}^n (\hat{y}_i - y_i) \mathbf{x}_i
\]
(derivación similar a la vista en semana 12, pero ahora es un vector). El gradiente respecto a \(b\) es \(\frac{1}{n} \sum (\hat{y}_i - y_i)\).

##### 3. Superficie de pérdida

La función de costo define una **superficie de pérdida** en el espacio de parámetros. Visualizarla (en 2D o 3D) ayuda a entender la optimización: mínimos locales, puntos de silla, etc. Por ejemplo, para una red neuronal simple, la superficie puede tener muchos valles.

#### Deep Learning (DL)

##### 1. Backpropagation (regla de la cadena multivariable)

El backpropagation es la aplicación sistemática de la regla de la cadena multivariable para calcular gradientes en redes profundas. Para una red con \(L\) capas, la pérdida es función de todas las matrices de pesos \(W^{(l)}\) y sesgos \(b^{(l)}\). El gradiente se propaga hacia atrás desde la salida hasta la entrada.

**Ejemplo con una red de dos capas (sin activación, solo lineal para simplificar):**
- \(z^{(1)} = W^{(1)} x + b^{(1)}\)
- \(z^{(2)} = W^{(2)} z^{(1)} + b^{(2)}\)
- \(\hat{y} = z^{(2)}\)
- \(L = \frac{1}{2} \|y - \hat{y}\|^2\)

Queremos \(\frac{\partial L}{\partial W^{(2)}}\). Primero, \(\frac{\partial L}{\partial \hat{y}} = -(y - \hat{y})\). Luego, \(\hat{y} = W^{(2)} z^{(1)} + b^{(2)}\), entonces \(\frac{\partial \hat{y}}{\partial W^{(2)}}\) es un tensor; en forma práctica, la derivada respecto a una matriz es un producto exterior: \(\frac{\partial L}{\partial W^{(2)}} = \frac{\partial L}{\partial \hat{y}} \cdot (z^{(1)})^T\). Esto es un producto de un vector fila (o columna) con un vector fila.

Para \(\frac{\partial L}{\partial W^{(1)}}\), necesitamos \(\frac{\partial L}{\partial z^{(1)}} = (W^{(2)})^T \frac{\partial L}{\partial \hat{y}}\) (por regla de la cadena). Luego, \(\frac{\partial L}{\partial W^{(1)}} = \frac{\partial L}{\partial z^{(1)}} \cdot x^T\).

##### 2. Gradiente en redes profundas

En redes profundas, el gradiente se calcula mediante multiplicaciones sucesivas de matrices jacobianas. Por ejemplo, en una red con varias capas, el gradiente de la pérdida respecto a los pesos de la primera capa implica productos de las matrices de pesos de capas superiores y derivadas de activaciones.

##### 3. Gradiente evanescente/explosivo (producto de Jacobianos)

Cuando se apilan muchas capas, el gradiente puede ser el producto de muchas matrices (las jacobianas de cada capa). Si estas matrices tienen autovalores < 1, el producto tiende a cero (**gradiente evanescente**); si > 1, tiende a infinito (**gradiente explosivo**). Esto dificulta el entrenamiento de redes muy profundas.

**Ejemplo:** Una red recurrente (RNN) sin control tiene el mismo problema. El gradiente a través de \(T\) pasos es el producto de \(T\) matrices \(W_{hh}^T\). Si los autovalores de \(W_{hh}\) son menores que 1, el gradiente decae exponencialmente.

##### 4. Optimizadores (Adam, etc.)

Los optimizadores modernos como Adam utilizan el gradiente (vector) y también estimaciones de momentos de primer y segundo orden (que involucran el gradiente al cuadrado, que es un tensor). La actualización de parámetros es:
\[
m_t = \beta_1 m_{t-1} + (1-\beta_1) \nabla L_t
\]
\[
v_t = \beta_2 v_{t-1} + (1-\beta_2) (\nabla L_t)^2
\]
\[
\theta_{t+1} = \theta_t - \eta \frac{m_t}{\sqrt{v_t} + \epsilon}
\]
Aquí, el gradiente \(\nabla L_t\) es un vector (o tensor aplanado). Las operaciones son elemento a elemento, pero conceptualmente se manejan como vectores.

##### 5. Análisis de la Hessiana en optimización

En optimización de redes neuronales, la matriz Hessiana (de segundas derivadas) es enorme, pero su análisis es útil teóricamente. Por ejemplo, la condición de los puntos de silla se relaciona con autovalores de la Hessiana. En la práctica, se usan aproximaciones (como en el método de Newton truncado o L-BFGS) que evitan calcular la Hessiana completa.

---

