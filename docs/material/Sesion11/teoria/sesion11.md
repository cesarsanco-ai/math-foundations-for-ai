## Semana 11: Límites y Continuidad

### Teoría

#### 1. Concepto de límite

##### Idea intuitiva

El límite de una función \(f(x)\) cuando \(x\) se aproxima a un valor \(a\) es el valor \(L\) al que se acerca \(f(x)\) a medida que \(x\) se acerca a \(a\), sin importar si \(f(a)\) está definido o es igual a \(L\).

**Ejemplo intuitivo:** Considera \(f(x) = \frac{x^2 - 1}{x - 1}\). Para \(x \neq 1\), podemos simplificar: \(f(x) = x + 1\). A medida que \(x\) se acerca a 1, \(f(x)\) se acerca a 2. Aunque \(f(1)\) no está definido (0/0), el límite cuando \(x \to 1\) es 2.

##### Definición formal (epsilon-delta)

Decimos que \(\lim_{x \to a} f(x) = L\) si para todo \(\epsilon > 0\) existe un \(\delta > 0\) tal que siempre que \(0 < |x - a| < \delta\), se cumple \(|f(x) - L| < \epsilon\).

Esta definición captura la idea de que podemos hacer que \(f(x)\) esté tan cerca de \(L\) como queramos, tomando \(x\) suficientemente cerca de \(a\) (pero no igual).

##### Límites laterales

A veces la función se comporta diferente al acercarse por la izquierda o por la derecha. Se definen:

- Límite por la izquierda: \(\lim_{x \to a^-} f(x)\)
- Límite por la derecha: \(\lim_{x \to a^+} f(x)\)

El límite existe si y solo si ambos límites laterales existen y son iguales.

**Ejemplo:** \(f(x) = \frac{|x|}{x}\). Para \(x \to 0^+\), \(f(x) = 1\); para \(x \to 0^-\), \(f(x) = -1\). Por tanto, \(\lim_{x \to 0} f(x)\) no existe.

##### Límites al infinito

También consideramos el comportamiento cuando \(x\) crece indefinidamente: \(\lim_{x \to \infty} f(x)\) o \(\lim_{x \to -\infty} f(x)\).

**Ejemplo:** \(\lim_{x \to \infty} \frac{1}{x} = 0\).

#### 2. Continuidad de funciones

##### Definición

Una función \(f\) es continua en un punto \(a\) si:

1. \(f(a)\) está definido.
2. \(\lim_{x \to a} f(x)\) existe.
3. \(\lim_{x \to a} f(x) = f(a)\).

Intuitivamente, no hay saltos ni interrupciones; se puede dibujar sin levantar el lápiz.

**Ejemplo:** \(f(x) = x^2\) es continua en todo \(\mathbb{R}\).  
\(f(x) = \begin{cases} x^2 & \text{si } x \neq 2 \\ 5 & \text{si } x = 2 \end{cases}\) no es continua en \(x=2\) porque el límite es 4 pero \(f(2)=5\).

##### Tipos de discontinuidades

- **Discontinuidad evitable (removible):** El límite existe pero no coincide con el valor de la función (o la función no está definida). Ejemplo: \(f(x) = \frac{x^2-1}{x-1}\) en \(x=1\).
- **Discontinuidad de salto:** Los límites laterales existen pero son diferentes. Ejemplo: \(f(x) = \frac{|x|}{x}\) en \(x=0\).
- **Discontinuidad infinita:** La función tiende a infinito cerca del punto. Ejemplo: \(f(x) = \frac{1}{x}\) en \(x=0\).
- **Discontinuidad esencial (oscilatoria):** No existe el límite por oscilación. Ejemplo: \(f(x) = \sin(1/x)\) en \(x=0\).

#### 3. Propiedades de funciones continuas

##### Teorema del valor intermedio

Si \(f\) es continua en un intervalo cerrado \([a, b]\) y \(k\) es cualquier número entre \(f(a)\) y \(f(b)\), entonces existe al menos un \(c \in [a, b]\) tal que \(f(c) = k\).

**Interpretación:** Una función continua no puede saltar de un valor a otro sin pasar por todos los intermedios.

**Ejemplo:** La función \(f(x) = x^3 - x\) en \([0,2]\). \(f(0)=0\), \(f(2)=6\). Para \(k=3\), debe existir un \(c\) tal que \(f(c)=3\). Efectivamente, \(c \approx 1.5\) (pues \(1.5^3 - 1.5 = 3.375 - 1.5 = 1.875\), no exacto; pero por el teorema, existe aunque no sea fácil de hallar analíticamente).

##### Teorema de los valores extremos (Weierstrass)

Si \(f\) es continua en un intervalo cerrado \([a, b]\), entonces \(f\) alcanza un máximo y un mínimo absolutos en ese intervalo.

**Ejemplo:** \(f(x) = x^2\) en \([-2, 2]\) tiene mínimo 0 en \(x=0\) y máximo 4 en \(x=\pm 2\).

#### 4. Comportamiento local y estabilidad

La continuidad implica que pequeños cambios en la entrada producen pequeños cambios en la salida. Esto es fundamental para la estabilidad de los modelos: si el modelo es continuo, entonces una pequeña perturbación en los datos no debería causar un cambio drástico en la predicción (salvo en puntos de no continuidad, como en funciones escalón).

En optimización, la continuidad de la función de pérdida asegura que el descenso de gradiente tenga sentido: movernos un poco en la dirección del gradiente debería reducir la pérdida localmente (si la función es diferenciable) o al menos no dar saltos bruscos.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Funciones de pérdida: necesidad de continuidad para optimización

Las funciones de pérdida en ML deben ser al menos continuas (y preferiblemente diferenciables) para poder aplicar métodos basados en gradiente. Si la función de pérdida tuviera discontinuidades, el gradiente no estaría definido en esos puntos y el algoritmo de optimización podría tener dificultades.

**Ejemplo:** El error cuadrático medio (MSE) es una función continua y diferenciable de los parámetros. En cambio, el error absoluto medio (MAE) es continua pero no diferenciable en 0 (aunque se puede manejar con subgradientes). Una función escalón (como el error 0-1 en clasificación) es discontinua, por eso no se usa directamente en optimización por gradiente.

**Ejemplo concreto:** En regresión lineal, la función de costo MSE:
\[
L(w) = \frac{1}{n} \sum_{i=1}^n (y_i - w x_i)^2
\]
es un polinomio en \(w\), por tanto continua y diferenciable. Esto permite usar gradiente descendente.

En cambio, si definiéramos una pérdida como:
\[
L(w) = \begin{cases}
0 & \text{si } |y - \hat{y}| < 0.5 \\
1 & \text{en otro caso}
\end{cases}
\]
sería discontinua y no podríamos optimizar con gradiente.

##### 2. Optimización y convergencia

La continuidad también juega un papel en la convergencia de algoritmos de optimización. Por ejemplo, el teorema de convergencia del gradiente descendente para funciones convexas y continuas garantiza que la sucesión de iteraciones converge al mínimo global. Si la función no es continua, podríamos tener problemas.

Además, en métodos de búsqueda de línea, se asume continuidad para asegurar que existe un punto que satisface las condiciones de Wolfe.

**Ejemplo:** En SVM con hinge loss, la función hinge loss \( \max(0, 1 - y f(x)) \) es continua (aunque no diferenciable en el punto donde el argumento es 0). Esto permite usar subgradientes.

#### Deep Learning (DL)

##### 1. Estabilidad de funciones de activación

Las funciones de activación deben ser continuas para que la red sea estable. Una discontinuidad podría causar que pequeñas variaciones en la entrada produzcan cambios abruptos en la salida, lo cual no es deseable.

- **ReLU:** \( \text{ReLU}(x) = \max(0, x) \) es continua en todo \(\mathbb{R}\) (aunque no diferenciable en 0). Esto es aceptable; de hecho, es la más usada.
- **Sigmoide:** \( \sigma(x) = 1/(1+e^{-x}) \) es continua y suave.
- **Tanh:** también continua y suave.
- **Step function (escalón):** No se usa en redes profundas por su discontinuidad, aunque en perceptrones originales sí se usaba (pero no permitía backpropagation).

**Ejemplo de inestabilidad:** Si usáramos una función de activación discontinua, como un escalón, un pequeño cambio en la entrada que cruce el umbral cambiaría la salida de 0 a 1 abruptamente, lo que dificulta el entrenamiento y hace que el modelo sea muy sensible.

##### 2. Convergencia del entrenamiento

El entrenamiento de redes neuronales se basa en la optimización de una función de pérdida que es composición de funciones continuas (y generalmente diferenciables a trozos). La continuidad de cada capa asegura que la función total sea continua, lo que permite que pequeñas actualizaciones de pesos produzcan pequeños cambios en la pérdida, facilitando la convergencia.

Además, en técnicas como _gradient clipping_, se aprovecha la continuidad para evitar que gradientes muy grandes (explosivos) desestabilicen el entrenamiento.

**Ejemplo:** En una red con activaciones ReLU, la función de pérdida es continua aunque no diferenciable en algunos puntos. Sin embargo, en la práctica, los algoritmos de optimización como Adam funcionan bien debido a que los puntos de no diferenciabilidad son un conjunto de medida cero y se pueden manejar con subgradientes.

##### 3. Regularización y estabilidad

La regularización L2 añade un término \(\lambda \|\theta\|^2\) que es continuo y diferenciable, lo que ayuda a mantener la estabilidad del modelo al penalizar pesos grandes. Sin continuidad, la regularización podría no tener el efecto suave deseado.

##### 4. Análisis de sensibilidad

En interpretabilidad, a veces se estudia cómo cambia la salida ante pequeñas perturbaciones en la entrada. Si el modelo es continuo, estas variaciones son controladas. Por ejemplo, en ataques adversarios, se busca una pequeña perturbación que cambie drásticamente la salida; si el modelo es continuo, esto requiere que la función tenga gradientes grandes, pero no saltos.

---

