## Módulo 1: Fundamentos de Espacios Vectoriales

### Definición y axiomas

Un **espacio vectorial** sobre los números reales $\mathbb{R}$ es un conjunto $V$ de elementos llamados **vectores**, junto con dos operaciones:

- **Suma** de vectores: $ \mathbf{u} + \mathbf{v} \in V $
- **Multiplicación por un escalar** (número real): $ \alpha \mathbf{v} \in V $, con $\alpha \in \mathbb{R}$

Estas operaciones cumplen ocho axiomas (asociatividad, conmutatividad, existencia del vector nulo $\mathbf{0}$, existencia de opuesto, distributividad, etc.). En la práctica, para IA basta con entender que:

> *Podemos sumar dos representaciones de datos y multiplicarlas por un número, y el resultado sigue siendo una representación válida en el mismo espacio.*

### Ejemplos relevantes en IA

1. **$\mathbb{R}^n$** (el espacio de las $n$-tuplas de números reales)  
   - **Vectores de características**: una persona se representa como $ \mathbf{x} = (edad, ingreso, num\_compras) \in \mathbb{R}^3$  
   - **Embeddings de palabras**: Word2Vec asigna a cada palabra un vector en $\mathbb{R}^{300}$  
   - **Pesos de una red neuronal**: capa con 784 entradas y 256 neuronas → matriz de pesos $W \in \mathbb{R}^{256 \times 784}$ cuyas filas/columnas son vectores.

2. **Espacios de funciones**  
   - Cada función $f: \mathbb{R} \to \mathbb{R}$ puede verse como un vector (infinito). En **SVM con kernels**, los datos se mapean a un espacio de funciones (RKHS) donde el producto interno es el kernel.

3. **Espacios de matrices**  
   - Una capa convolucional puede representarse como una matriz de Toeplitz; los filtros son vectores en ese espacio.

### ¿Por qué es importante?

Todo dato que alimenta un modelo de IA se representa como un vector. Las operaciones que hacemos (similaridad, clasificación, generación) ocurren dentro de estos espacios. Sin entenderlos, no se puede interpretar ni depurar un modelo.

#### Ejemplo sencillo (concreto)

Imagina que clasificamos frutas usando dos características: peso (gramos) y dulzor (del 0 al 10). Cada fruta es un vector en $\mathbb{R}^2$:

$$ \text{Manzana} = \begin{pmatrix} 150 \\ 7 \end{pmatrix}, \quad \text{Naranja} = \begin{pmatrix} 140 \\ 8 \end{pmatrix}, \quad \text{Plátano} = \begin{pmatrix} 120 \\ 6 \end{pmatrix} $$

- **Suma de vectores**: $ \text{Manzana} + \text{Naranja} = (290, 15) $ no tiene sentido físico como fruta, pero sí como agregación de dos muestras (por ejemplo, para promediar).
- **Multiplicación por escalar**: $ 0.5 \cdot \text{Manzana} = (75, 3.5) $ podría interpretarse como una fruta “media manzana” (útil para interpolar).

**Interpretación**: Aunque las operaciones son abstractas, nos permiten manipular datos de forma algebraica, esencial para algoritmos como K‑medias o PCA.

---

## Módulo 2: Subespacios Vectoriales

### Definición

Un **subespacio vectorial** $U$ de $V$ es un subconjunto no vacío de $V$ que a su vez es un espacio vectorial con las mismas operaciones. Equivalentemente, $U$ es cerrado bajo:

- **Suma**: $\forall \mathbf{u}, \mathbf{v} \in U,\; \mathbf{u}+\mathbf{v} \in U$
- **Multiplicación por escalar**: $\forall \alpha \in \mathbb{R},\; \forall \mathbf{u} \in U,\; \alpha\mathbf{u} \in U$

*Consecuencia*: el vector nulo $\mathbf{0}$ siempre pertenece a $U$.

### Subespacios clave en IA

1. **Espacio generado por los datos (span)**  
   Dado un conjunto de vectores $\mathbf{v}_1, \dots, \mathbf{v}_k$, su **span** es el conjunto de todas las combinaciones lineales:
   $$ \text{span}\{\mathbf{v}_1, \dots, \mathbf{v}_k\} = \left\{ \sum_{i=1}^k \alpha_i \mathbf{v}_i \;\middle|\; \alpha_i \in \mathbb{R} \right\} $$
   Este subespacio define todo lo que el modelo puede representar con esos datos. Si los datos son redundantes, el span tiene dimensión menor.

2. **Espacio latente**  
   En autoencoders, GANs y modelos de difusión, el **espacio latente** es un subespacio (o variedad) de baja dimensión donde se codifican los atributos esenciales de los datos. Por ejemplo, un espacio latente de 2 dimensiones para caras humanas podría representar: `(orientación, expresión)`.

### Aplicación práctica

- **GenAI (interpolación)**: En el espacio latente de StyleGAN, cada punto genera una imagen. Interpolar entre dos puntos latentes $\mathbf{z}_1$ y $\mathbf{z}_2$ mediante combinaciones convexas:
  $$ \mathbf{z}(t) = (1-t)\mathbf{z}_1 + t\mathbf{z}_2, \quad t \in [0,1] $$
  produce una transición suave y realista entre las dos imágenes generadas.

- **Reducción implícita de dimensionalidad**: Una red neuronal profunda, capa por capa, proyecta los datos en subespacios de menor dimensión (cuando el número de neuronas disminuye). Esto fuerza al modelo a aprender las direcciones más informativas, ignorando el ruido.

### Ejemplo sencillo con interpretación

Supongamos que tenemos solo dos vectores de características de clientes:

$$ \mathbf{a} = \begin{pmatrix} 1 \\ 2 \end{pmatrix}, \quad \mathbf{b} = \begin{pmatrix} 2 \\ 4 \end{pmatrix} $$

Observamos que $\mathbf{b} = 2\mathbf{a}$, es decir, son linealmente dependientes. Entonces:

$$ \text{span}\{\mathbf{a}, \mathbf{b}\} = \text{span}\{\mathbf{a}\} = \{ \alpha \begin{pmatrix} 1 \\ 2 \end{pmatrix} \mid \alpha \in \mathbb{R} \} $$

Geométricamente, es la recta que pasa por el origen con pendiente 2. **Interpretación en IA**: si dos características son proporcionales (ej. “precio en dólares” y “precio en euros” con tipo de cambio fijo), el subespacio real de los datos es unidimensional, no bidimensional. El modelo no necesita ambas; puede trabajar solo con una. Detectar esta redundancia evita overfitting y acelera el entrenamiento.

**Otro ejemplo (espacio latente)**:  
Imagina un conjunto de imágenes de dígitos escritos a mano (MNIST). Un autoencoder aprende un espacio latente de 2 dimensiones. Cada dígito se convierte en un punto $(z_1, z_2)$. Si tomamos el punto correspondiente a un "4" y el de un "9", la recta que los une contiene puntos intermedios que generan dígitos con forma mezclada. Aunque esos puntos intermedios no sean dígitos reales, el subespacio (la recta) es una **línea dentro del espacio latente** donde el modelo puede explorar variaciones continuas.

**Conclusión del módulo**: Un subespacio es un “plano” (recta, plano, hiperplano) que pasa por el origen. Todo modelo lineal trabaja dentro de subespacios; los modelos no lineales a menudo aprenden subespacios curvos (variedades), pero la base conceptual es la misma.




---

## Módulo 3: Combinaciones Lineales, Span e Independencia Lineal

### 3.1 Combinación lineal

**Definición**: Dados un conjunto de vectores $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k$ en un espacio vectorial $V$, y escalares $c_1, c_2, \dots, c_k \in \mathbb{R}$, el vector  
$$ \mathbf{w} = c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \dots + c_k\mathbf{v}_k $$  
se denomina **combinación lineal** de los vectores dados.

**Ejemplo sencillo (datos de ventas)**:  
Supongamos que las ventas de tres productos se representan con los vectores:  
$$ \mathbf{p}_1 = (100, 50) \quad (\text{producto A: 100 uds. en tienda1, 50 en tienda2}) $$  
$$ \mathbf{p}_2 = (80, 120) \quad (\text{producto B}) $$  
$$ \mathbf{p}_3 = (60, 90) \quad (\text{producto C}) $$  
Una combinación lineal $0.5\mathbf{p}_1 + 0.3\mathbf{p}_2 - 0.2\mathbf{p}_3$ podría representar una estrategia de reasignación de inventario.

**Interpretación en IA**:  
En una red neuronal, la salida de una capa es una combinación lineal de las entradas más un sesgo (transformación afín). En embeddings, las palabras se representan como combinaciones lineales de características latentes.

---

### 3.2 Span (conjunto generador)

**Definición**: El **span** (o conjunto generador) de un conjunto de vectores $S = \{\mathbf{v}_1, \dots, \mathbf{v}_k\}$ es el conjunto de todas las combinaciones lineales posibles de esos vectores:  
$$ \operatorname{span}(S) = \left\{ \sum_{i=1}^k c_i \mathbf{v}_i \;\middle|\; c_i \in \mathbb{R} \right\} $$  
El span es siempre un subespacio vectorial de $V$.

**Ejemplo sencillo**:  
En $\mathbb{R}^2$, sean $\mathbf{v}_1 = (1,0)$ y $\mathbf{v}_2 = (0,1)$. Entonces $\operatorname{span}\{\mathbf{v}_1, \mathbf{v}_2\} = \mathbb{R}^2$ (todo el plano).  
Si solo tenemos $\mathbf{v}_1 = (1,0)$, entonces $\operatorname{span}\{\mathbf{v}_1\} = \{(x,0) \mid x \in \mathbb{R}\}$, el eje $x$.

**Interpretación en IA**:  
- El span de los vectores de entrenamiento define el subespacio donde vive el modelo lineal. Si los datos no generan todo $\mathbb{R}^d$, el modelo no puede representar vectores fuera de ese subespacio (sesgo inductivo).  
- En **sistemas de recomendación**, el span de los perfiles de usuario determina qué gustos pueden ser modelados.

---

### 3.3 Independencia lineal

**Definición**: Un conjunto de vectores $\{\mathbf{v}_1, \dots, \mathbf{v}_k\}$ es **linealmente independiente** si la única combinación lineal que da el vector nulo es aquella con todos los coeficientes cero:  
$$ c_1\mathbf{v}_1 + \dots + c_k\mathbf{v}_k = \mathbf{0} \;\Longrightarrow\; c_1 = \dots = c_k = 0 $$  
Si existe una combinación no trivial (con algún $c_i \neq 0$) que da $\mathbf{0}$, entonces los vectores son **linealmente dependientes**. En dependencia, al menos un vector se puede escribir como combinación lineal de los demás.

**Propiedad clave**: En un espacio de dimensión $n$, a lo sumo $n$ vectores pueden ser linealmente independientes.

**Ejemplo sencillo**:  
En $\mathbb{R}^3$, los vectores $(1,0,0)$, $(0,1,0)$, $(1,1,0)$ son linealmente dependientes porque $(1,1,0) = (1,0,0)+(0,1,0)$.  
Los vectores $(1,0,0)$, $(0,1,0)$, $(0,0,1)$ son independientes.

**Aplicaciones en IA**:

#### a) Detección de redundancia en características
Si en un dataset dos características son linealmente dependientes (por ejemplo, “precio en dólares” y “precio en euros” con tipo de cambio fijo), entonces una de ellas es superflua. La independencia lineal ayuda a identificar features redundantes, reduciendo la dimensionalidad y evitando la multicolinealidad en regresión.

#### b) Embeddings semánticos
En Word2Vec o GloVe, se busca que las dimensiones del espacio de embedding sean lo más independientes posible para que cada coordenada capture un aspecto semántico diferente (género, número, tiempo verbal, etc.). La independencia lineal permite desenredar (disentangle) los factores de variación.

#### c) Regularización (conexión indirecta)
Técnicas como **dropout** o **regularización de correlaciones** (por ejemplo, *orthogonal regularization*) fomentan que los pesos de una red sean aproximadamente independientes, mejorando la generalización.

---

### 3.4 Ejercicios integrados (solo enunciados para practicar)

1. Determina si los vectores $(2, -1, 3)$, $(1, 0, 1)$ y $(0, 2, -1)$ son linealmente independientes en $\mathbb{R}^3$.  
2. Encuentra el span de $\{(1,2), (2,4)\}$ y da su dimensión. ¿Qué problema práctico representa en un sistema de recomendación?  
3. Supón que en un modelo de NLP los embeddings de “gato”, “felino” y “perro” cumplen: $\text{gato} = 0.8\,\text{felino} + 0.2\,\text{perro}$. ¿Qué puedes concluir sobre la independencia lineal de estos tres vectores?

---

## Módulo 4: Bases, Dimensión y Cambio de Base

### 4.1 Base de un espacio vectorial

**Definición**: Un conjunto $B = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ es una **base** de $V$ si:  
1. $B$ es linealmente independiente.  
2. $B$ genera todo $V$ (es decir, $\operatorname{span}(B) = V$).

**Propiedad fundamental**: Cualquier vector $\mathbf{v} \in V$ se puede expresar de **forma única** como combinación lineal de los vectores de la base:  
$$ \mathbf{v} = \alpha_1 \mathbf{b}_1 + \dots + \alpha_n \mathbf{b}_n $$  
Los escalares $\alpha_i$ se llaman **coordenadas** de $\mathbf{v}$ en la base $B$.

**Ejemplo sencillo**:  
En $\mathbb{R}^2$, la base canónica es $B_c = \{(1,0), (0,1)\}$. El vector $(3, -2)$ tiene coordenadas $(3, -2)$.  
Otra base: $B' = \{(1,1), (1,-1)\}$. Entonces $(3,-2) = \frac{1}{2}(1,1) + \frac{5}{2}(1,-1)$; las coordenadas son $(\frac12, \frac52)$.

**Interpretación en IA**:  
- Las bases definen sistemas de coordenadas. En **reducción de dimensionalidad** (como PCA, que verás después), se busca una nueva base donde los datos estén mejor representados.  
- En **redes neuronales**, los pesos de una capa pueden interpretarse como la expresión de las salidas en la base de las entradas.

---

### 4.2 Dimensión

**Definición**: La **dimensión** de un espacio vectorial $V$ es el número de vectores en cualquier base de $V$. Se denota $\dim(V)$.  
- Si $\dim(V) = n$, entonces cualquier conjunto con más de $n$ vectores es linealmente dependiente.  
- Un subespacio $U \subseteq V$ cumple $\dim(U) \le \dim(V)$.

**Ejemplo**: $\dim(\mathbb{R}^n) = n$. El subespacio de los vectores con primera coordenada $0$ tiene dimensión $n-1$.

**Interpretación en IA**:  
- La dimensión del espacio de características es el número de atributos por muestra.  
- La **maldición de la dimensionalidad** aparece cuando $\dim$ es grande (ej. 1000), pues los datos se vuelven esparcidos.  
- En **espacios latentes** de modelos generativos, se elige una dimensión pequeña (ej. 128) para forzar al modelo a aprender una representación compacta.

---

### 4.3 Cambio de base

**Definición**: Dadas dos bases $B = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ y $C = \{\mathbf{c}_1, \dots, \mathbf{c}_n\}$ de $V$, existe una matriz **invertible** $P$ (llamada matriz de cambio de base) tal que para cualquier vector $\mathbf{v}$:  
$$ [\mathbf{v}]_C = P\; [\mathbf{v}]_B $$  
donde $[\mathbf{v}]_B$ es el vector de coordenadas de $\mathbf{v}$ en base $B$.  
Las columnas de $P$ son las coordenadas de los vectores de $B$ expresados en la base $C$.

**Fórmula práctica**: Si se conoce la expresión de los nuevos vectores base en términos de los antiguos, se construye $P$ fácilmente.

**Ejemplo sencillo**:  
En $\mathbb{R}^2$, base $B = \{(1,0), (0,1)\}$ (canónica) y base $C = \{(1,1), (1,-1)\}$.  
Para un vector $\mathbf{v} = (x,y)$ en base canónica, sus coordenadas en $C$ vienen dadas por:  
$$ [\mathbf{v}]_C = \begin{pmatrix} \frac{x+y}{2} \\ \frac{x-y}{2} \end{pmatrix} $$  
La matriz de cambio de base (de $B$ a $C$) es:  
$$ P = \begin{pmatrix} \frac12 & \frac12 \\ \frac12 & -\frac12 \end{pmatrix} $$

**Aplicaciones en IA**:

#### a) Embeddings y visualización
Los embeddings de palabras (Word2Vec, GloVe, BERT) viven en una base de alta dimensión (300, 768). Para visualizarlos en 2D se aplica un cambio de base (por ejemplo, con PCA o t‑SNE). Aunque PCA no es lineal exactamente (es una proyección ortogonal), la idea es similar: representar los vectores en una nueva base que maximice la varianza.

#### b) Kernels en SVM
El **truco del kernel** consiste en aplicar un cambio de base implícito (a veces a un espacio de dimensión infinita) mediante una función $\phi$. El producto interno en el nuevo espacio se calcula con el kernel:  
$$ K(\mathbf{x}, \mathbf{y}) = \langle \phi(\mathbf{x}), \phi(\mathbf{y}) \rangle $$  
Esto permite separar datos que no son linealmente separables en el espacio original, sin calcular explícitamente $\phi(\mathbf{x})$. Es un cambio de base no lineal (pero el nuevo espacio sigue siendo vectorial).

#### c) Espacio latente en GenAI
En un modelo generativo (VAE, GAN, difusión), el espacio latente $\mathbb{R}^d$ suele tener una base ortonormal estándar. Sin embargo, durante el entrenamiento, el modelo aprende una base implícita (los ejes principales de la variedad de datos). Al modificar las coordenadas en esa base, se controlan atributos específicos de la salida (sonrisa, color de pelo, estilo artístico). Por ejemplo, en StyleGAN, existe una base “disentangled” que permite editar independientemente cada atributo.

#### d) Normalización y estandarización
Estandarizar características (media 0, desviación 1) equivale a un cambio de base que reescala los ejes. La nueva base sigue siendo ortogonal pero las unidades son desviaciones típicas.

---

### 4.4 Ejercicios integrados (solo enunciados)

1. Encuentra una base para el subespacio $U = \{(x,y,z) \in \mathbb{R}^3 \mid x - y + 2z = 0\}$. ¿Cuál es su dimensión?  
2. Dada la base $B = \{(1,0), (1,2)\}$ de $\mathbb{R}^2$, expresa el vector $\mathbf{v} = (3,4)$ en coordenadas de $B$.  
3. En un espacio de embeddings de 3 dimensiones, se tienen dos bases: $B$ (canónica) y $C$ (aprendida por un modelo). La matriz de cambio de base de $B$ a $C$ es  
   $$ P = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{pmatrix} $$  
   Si un concepto “rey” tiene coordenadas $[2, 1, 0]^T$ en $C$, ¿cuáles son sus coordenadas en la base canónica?  

---

## Resumen de conceptos clave (Módulos 3 y 4)

| Concepto | Definición breve | Aplicación en IA |
|----------|----------------|------------------|
| Combinación lineal | $c_1\mathbf{v}_1+\dots+c_k\mathbf{v}_k$ | Capas lineales de redes, mezcla de embeddings |
| Span | Todas las combinaciones lineales | Subespacio alcanzable por un modelo lineal |
| Independencia lineal | Solo combinación trivial da cero | Detección de features redundantes, desenredo de factores |
| Base | Conjunto l.i. que genera el espacio | Sistema de coordenadas para representar datos |
| Dimensión | Número de vectores en una base | Complejidad del espacio (maldición de la dimensionalidad) |
| Cambio de base | Matriz que transforma coordenadas | Kernels, visualización de embeddings, espacios latentes |

---




## Módulo 5: Espacios con Producto Interno – Geometría para la IA

### 5.1 Producto interno (producto escalar)

**Definición**: En $\mathbb{R}^n$, el producto interno estándar (dot product) de dos vectores $\mathbf{u} = (u_1,\dots,u_n)$ y $\mathbf{v} = (v_1,\dots,v_n)$ es:
$$ \langle \mathbf{u}, \mathbf{v} \rangle = \mathbf{u} \cdot \mathbf{v} = u_1 v_1 + u_2 v_2 + \dots + u_n v_n $$
Geométricamente, mide cuánto se alinean: $\langle \mathbf{u}, \mathbf{v} \rangle = \|\mathbf{u}\| \|\mathbf{v}\| \cos\theta$, donde $\theta$ es el ángulo entre ellos.

**Propiedades**:
- Simetría: $\langle \mathbf{u}, \mathbf{v} \rangle = \langle \mathbf{v}, \mathbf{u} \rangle$
- Linealidad: $\langle \alpha \mathbf{u} + \beta \mathbf{w}, \mathbf{v} \rangle = \alpha \langle \mathbf{u}, \mathbf{v} \rangle + \beta \langle \mathbf{w}, \mathbf{v} \rangle$
- Definido positivo: $\langle \mathbf{v}, \mathbf{v} \rangle \ge 0$, y es $0$ solo si $\mathbf{v} = \mathbf{0}$.

**Ejemplo sencillo**:  
$\mathbf{u} = (2, -1)$, $\mathbf{v} = (3, 4)$ → $\langle \mathbf{u}, \mathbf{v} \rangle = 2\cdot3 + (-1)\cdot4 = 6 - 4 = 2$.

**Interpretación en IA**:  
- En **mecanismo de atención** (Transformers), la atención se calcula como $\text{softmax}(\mathbf{Q}\mathbf{K}^T/\sqrt{d_k})$, donde cada entrada es un producto interno entre queries y keys.  
- En **redes neuronales**, el cómputo de una neurona es $\langle \mathbf{w}, \mathbf{x} \rangle + b$.

---

### 5.2 Norma (longitud de un vector)

**Definición**: Una norma $\|\cdot\|$ asigna a cada vector un número no negativo que mide su magnitud. Las más usadas en IA:

#### Norma L2 (euclidiana)
$$ \|\mathbf{v}\|_2 = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2} = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle} $$
Es la distancia euclidiana al origen.

#### Norma L1 (Manhattan)
$$ \|\mathbf{v}\|_1 = |v_1| + |v_2| + \dots + |v_n| $$
Suma de los valores absolutos.

#### Norma L∞ (máximo o Chebyshev)
$$ \|\mathbf{v}\|_\infty = \max(|v_1|, |v_2|, \dots, |v_n|) $$
La componente más grande en valor absoluto.

**Ejemplo**: $\mathbf{v} = (3, -4)$ → $\|\mathbf{v}\|_2 = 5$, $\|\mathbf{v}\|_1 = 7$, $\|\mathbf{v}\|_\infty = 4$.

**Interpretación geométrica**:  
Cada norma define una **bola unitaria** $B_p = \{\mathbf{v} : \|\mathbf{v}\|_p \le 1\}$:
- L2 → círculo (esfera)
- L1 → rombo (diamante)
- L∞ → cuadrado alineado a los ejes

Estas formas determinan cómo se mide la distancia y afectan algoritmos como KNN, regularización y SVM.

---

### 5.3 Distancias comunes en IA

Dados dos vectores $\mathbf{x}, \mathbf{y}$, la distancia se define a partir de una norma (o de una función de similitud):

| Distancia | Fórmula | Cuándo usarla en IA |
|-----------|---------|----------------------|
| Euclidiana (L2) | $d_2(\mathbf{x},\mathbf{y}) = \|\mathbf{x}-\mathbf{y}\|_2$ | Características continuas, escalas similares, pocas dimensiones. |
| Manhattan (L1) | $d_1(\mathbf{x},\mathbf{y}) = \|\mathbf{x}-\mathbf{y}\|_1$ | Datos de alta dimensión, presencia de outliers, características binarias. |
| Chebyshev (L∞) | $d_\infty(\mathbf{x},\mathbf{y}) = \|\mathbf{x}-\mathbf{y}\|_\infty$ | Problemas donde la peor diferencia importa (ej. tableros de ajedrez). |
| Coseno | $d_{\cos}(\mathbf{x},\mathbf{y}) = 1 - \cos\theta = 1 - \frac{\langle \mathbf{x},\mathbf{y} \rangle}{\|\mathbf{x}\|_2\|\mathbf{y}\|_2}$ | Embeddings (textos, imágenes, recomendaciones); ignora la magnitud. |

**Propiedad importante**: La distancia coseno no es una norma porque no cumple la desigualdad triangular, pero es muy útil para vectores normalizados.

**Ejemplo**:  
$\mathbf{x} = (1,2)$, $\mathbf{y} = (2,4)$ → $\|\mathbf{x}-\mathbf{y}\|_2 = \sqrt{( -1)^2 + (-2)^2} = \sqrt{5} \approx 2.236$;  
$\|\mathbf{x}-\mathbf{y}\|_1 = 1+2 = 3$;  
$\cos\theta = \frac{1\cdot2+2\cdot4}{\sqrt{1+4}\sqrt{4+16}} = \frac{2+8}{\sqrt{5}\sqrt{20}} = \frac{10}{10} = 1$ → distancia coseno = 0 (misma dirección).

---

### 5.4 Aplicaciones directas en IA

#### 🔹 K‑vecinos más cercanos (KNN)
KNN clasifica un punto según la mayoría de sus $k$ vecinos más cercanos según una distancia. La elección de la distancia es crítica:

- **L2 (Euclidiana)**: adecuada cuando todas las características tienen la misma escala y no hay outliers extremos. Ejemplo: coordenadas espaciales.
- **L1 (Manhattan)**: más robusta en alta dimensión porque no magnifica diferencias grandes tanto como L2. Útil para datos de texto con muchas dimensiones dispersas (bolsa de palabras).
- **Coseno**: ideal para embeddings normalizados (Word2Vec, BERT, imágenes). Ignora la longitud, captura solo la orientación semántica.

**Ejemplo práctico**: En un sistema de recomendación de películas, los usuarios se representan por vectores de gustos normalizados. Usar distancia coseno permite encontrar usuarios con gustos similares aunque unos valoren más alto en general.

#### 🔹 Regularización L1 y L2 (weight decay)
La función de pérdida total en un modelo lineal (o red neuronal) añade un término de penalización:
$$ \text{Loss} = \text{Error}(y, \hat{y}) + \lambda \|\mathbf{w}\|_p $$
- **L2 (Ridge)**: $\lambda \|\mathbf{w}\|_2^2$. Penaliza pesos grandes, pero nunca los hace exactamente cero. Geometría: la región factible es una bola L2.
- **L1 (Lasso)**: $\lambda \|\mathbf{w}\|_1$. Induce **sparsity** (muchos pesos se vuelven cero) porque la bola L1 tiene esquinas en los ejes. Útil para selección de características.

**Interpretación geométrica**: Minimizar la pérdida original sujeta a $\|\mathbf{w}\|_p \le t$ (o de forma equivalente añadir $\lambda$) equivale a buscar el punto de la bola $p$ que toca primero las curvas de nivel del error. La bola L1 (rombo) hace que el contacto ocurra a menudo en un eje → pesos cero.

#### 🔹 SVM lineal (Máquinas de Vectores Soporte)
El SVM lineal encuentra un hiperplano $\mathbf{w}^T \mathbf{x} + b = 0$ que separa dos clases con el máximo **margen**. El margen es $2 / \|\mathbf{w}\|_2$. Maximizar el margen equivale a minimizar $\|\mathbf{w}\|_2^2$. Por tanto, el SVM lineal es intrínsecamente una regularización L2 sobre el vector normal.

**Ecuación de optimización** (sin holgura):
$$ \min_{\mathbf{w}, b} \frac{1}{2} \|\mathbf{w}\|_2^2 \quad \text{sujeto a} \quad y_i (\mathbf{w}^T \mathbf{x}_i + b) \ge 1 \quad \forall i $$

---

### 5.5 Ejercicios propuestos (Módulo 5)

1. Calcula las normas L1, L2 y L∞ del vector $\mathbf{v} = (2, -3, 1)$.  
2. Dados $\mathbf{a} = (1, 0, 1)$ y $\mathbf{b} = (0, 1, 1)$, halla la distancia euclidiana, Manhattan y coseno.  
3. ¿Por qué en KNN con embeddings de frases se prefiere distancia coseno en lugar de Euclidiana? Razona.  
4. Dibuja (mentalmente) la bola unitaria en $\mathbb{R}^2$ para L1, L2 y L∞. Explica cómo la forma de la bola L1 provoca soluciones sparse en regularización.  
5. En un SVM lineal, ¿qué sucede si se aumenta el parámetro de regularización $C$ (que es inverso a $\lambda$)? Relaciona con la norma de $\mathbf{w}$.

---

## Módulo 6: Ortogonalidad, Proyecciones y Descomposición Ortogonal

### 6.1 Ortogonalidad y ortonormalidad

**Definición**: Dos vectores $\mathbf{u}, \mathbf{v}$ son **ortogonales** (o perpendiculares) si $\langle \mathbf{u}, \mathbf{v} \rangle = 0$. Un conjunto de vectores es **ortonormal** si son mutuamente ortogonales y cada uno tiene norma 1: $\langle \mathbf{u}_i, \mathbf{u}_j \rangle = \delta_{ij}$ (delta de Kronecker).

**Ejemplo**: En $\mathbb{R}^3$, los vectores $\mathbf{e}_1=(1,0,0)$, $\mathbf{e}_2=(0,1,0)$, $\mathbf{e}_3=(0,0,1)$ son ortonormales.

**Propiedad**: Si los vectores son ortogonales, el teorema de Pitágoras se generaliza: $\|\mathbf{u} + \mathbf{v}\|^2 = \|\mathbf{u}\|^2 + \|\mathbf{v}\|^2$ cuando $\langle \mathbf{u}, \mathbf{v} \rangle = 0$.

**Interpretación en IA**:  
- En **redes neuronales**, se ha propuesto la regularización de ortogonalidad para evitar que las columnas de las matrices de pesos sean redundantes (mejora el flujo de gradientes).  
- En **mecanismos de atención**, las queries y keys pueden normalizarse para que tengan norma 1, y la atención se convierte en un producto interno que mide la similitud coseno.

---

### 6.2 Proyección ortogonal

**Definición**: Dado un vector $\mathbf{v}$ y un subespacio $S$, la **proyección ortogonal** de $\mathbf{v}$ sobre $S$ es el único vector $\mathbf{p} \in S$ tal que $\mathbf{v} - \mathbf{p}$ es ortogonal a todos los vectores de $S$ (es decir, $\mathbf{v} - \mathbf{p} \perp S$).  
$\mathbf{p}$ es el punto de $S$ más cercano a $\mathbf{v}$ en distancia L2.

**Fórmula (caso 1D)**: Si $S$ es la recta generada por $\mathbf{a} \neq \mathbf{0}$, entonces:
$$ \mathbf{p} = \operatorname{proy}_{\mathbf{a}}(\mathbf{v}) = \frac{\langle \mathbf{v}, \mathbf{a} \rangle}{\langle \mathbf{a}, \mathbf{a} \rangle} \mathbf{a} $$
**Caso general (base ortonormal)**: Si $\{\mathbf{u}_1, \dots, \mathbf{u}_k\}$ es una base ortonormal de $S$, entonces:
$$ \mathbf{p} = \sum_{i=1}^k \langle \mathbf{v}, \mathbf{u}_i \rangle \mathbf{u}_i $$

**Ejemplo**: Proyectar $\mathbf{v} = (3,4)$ sobre el eje $x$ (subespacio generado por $(1,0)$): $\mathbf{p} = (3,0)$.

**Interpretación geométrica**: La proyección es la "sombra" de $\mathbf{v}$ sobre el subespacio cuando la luz incide perpendicularmente.

---

### 6.3 Proceso de Gram‑Schmidt

**Objetivo**: Dada una base $\{\mathbf{v}_1, \dots, \mathbf{v}_k\}$ de un subespacio, construir una base **ortonormal** $\{\mathbf{u}_1, \dots, \mathbf{u}_k\}$.

**Algoritmo**:
1. $\mathbf{u}_1 = \frac{\mathbf{v}_1}{\|\mathbf{v}_1\|}$
2. Para $i = 2$ a $k$:
   - $\mathbf{w}_i = \mathbf{v}_i - \sum_{j=1}^{i-1} \langle \mathbf{v}_i, \mathbf{u}_j \rangle \mathbf{u}_j$
   - $\mathbf{u}_i = \frac{\mathbf{w}_i}{\|\mathbf{w}_i\|}$

**Ejemplo**: En $\mathbb{R}^2$, $\mathbf{v}_1=(1,1)$, $\mathbf{v}_2=(1,0)$.  
- $\mathbf{u}_1 = \frac{(1,1)}{\sqrt{2}} = (1/\sqrt{2}, 1/\sqrt{2})$  
- $\mathbf{w}_2 = (1,0) - \langle (1,0), \mathbf{u}_1 \rangle \mathbf{u}_1 = (1,0) - \frac{1}{\sqrt{2}} (1/\sqrt{2}, 1/\sqrt{2}) = (1,0) - (0.5, 0.5) = (0.5, -0.5)$  
- $\mathbf{u}_2 = \frac{(0.5, -0.5)}{0.5\sqrt{2}} = (1/\sqrt{2}, -1/\sqrt{2})$  
Efectivamente $\langle \mathbf{u}_1, \mathbf{u}_2 \rangle = 0$ y ambos tienen norma 1.

**Aplicación en IA**:  
- En **reducción de dimensionalidad** (PCA) se obtienen componentes principales que son ortonormales.  
- En **métodos de kernel** a veces se ortogonalizan características.  
- En **redes neuronales**, algunas técnicas inicializan pesos con matrices ortogonales (por ejemplo, inicialización ortogonal) para evitar la desaparición/explosión del gradiente.

---

### 6.4 Aplicaciones en IA

#### 🔹 Regresión lineal (mínimos cuadrados)
Dado un conjunto de puntos $(\mathbf{x}_i, y_i)$, la regresión lineal busca $\mathbf{w}$ que minimice $\sum_i (y_i - \mathbf{w}^T \mathbf{x}_i)^2$. En forma matricial, $\mathbf{y} = X\mathbf{w} + \boldsymbol{\varepsilon}$. La solución óptima es la proyección ortogonal de $\mathbf{y}$ sobre el espacio columna de $X$:  
$$ \mathbf{w} = (X^T X)^{-1} X^T \mathbf{y} $$  
Geométricamente, $\hat{\mathbf{y}} = X\mathbf{w}$ es la proyección de $\mathbf{y}$ sobre el subespacio generado por las columnas de $X$. El residuo $\mathbf{y} - \hat{\mathbf{y}}$ es ortogonal a ese subespacio.

#### 🔹 Kernels y espacios RKHS (Reproducing Kernel Hilbert Space)
En SVM con kernel, los datos se mapean implícitamente a un espacio de funciones (RKHS) donde el producto interno es el kernel $K(\mathbf{x}, \mathbf{z}) = \langle \phi(\mathbf{x}), \phi(\mathbf{z}) \rangle$. La ortogonalidad en ese espacio permite separar clases que no son linealmente separables en el espacio original. Por ejemplo, el kernel RBF $\exp(-\gamma \|\mathbf{x}-\mathbf{z}\|^2)$ corresponde a un espacio de dimensión infinita; dos puntos pueden ser ortogonales en ese espacio aunque no lo sean en $\mathbb{R}^n$.

#### 🔹 Eliminación de ruido (autoencoders lineales)
Supongamos que los datos limpios viven en un subespacio $S$ de baja dimensión, y el ruido es ortogonal a $S$ (o al menos no correlacionado). La proyección ortogonal sobre $S$ elimina la componente de ruido. Esta es la base del **análisis de componentes principales** (PCA, que verás después) y de los autoencoders lineales.

**Ejemplo**: Imágenes de caras con ruido. Si las caras limpias ocupan un subespacio de dimensión 100 en un espacio de 1024 píxeles, proyectar una imagen ruidosa sobre ese subespacio reduce drásticamente el ruido.

---

### 6.5 Ejercicios propuestos (Módulo 6)

1. Comprueba que los vectores $(1,2,-1)$ y $(2,-1,0)$ son ortogonales. Calcula la proyección del primero sobre el segundo.  
2. Dados $\mathbf{v}_1 = (1,1,0)$, $\mathbf{v}_2 = (1,0,1)$, $\mathbf{v}_3 = (0,1,1)$. Aplica Gram‑Schmidt para obtener una base ortonormal del subespacio que generan.  
3. En regresión lineal, ¿por qué la solución de mínimos cuadrados se interpreta como una proyección ortogonal? Dibuja un ejemplo en $\mathbb{R}^2$ con dos puntos.  
4. Explica por qué el kernel RBF puede considerarse un producto interno en un espacio de dimensión infinita. ¿Qué papel juega la ortogonalidad en la separación de clases?  
5. Un autoencoder lineal con capa de codificación de dimensión $d$ y decodificación que reconstruye la entrada. ¿Cómo se relaciona la reconstrucción con la proyección ortogonal sobre el subespacio de la capa oculta?

---

## Resumen de fórmulas clave (Módulos 5 y 6)

| Concepto | Expresión |
|----------|-----------|
| Producto interno | $\langle \mathbf{u}, \mathbf{v} \rangle = \sum u_i v_i$ |
| Norma L2 | $\|\mathbf{v}\|_2 = \sqrt{\sum v_i^2}$ |
| Norma L1 | $\|\mathbf{v}\|_1 = \sum |v_i|$ |
| Norma L∞ | $\|\mathbf{v}\|_\infty = \max |v_i|$ |
| Distancia coseno | $d_{\cos} = 1 - \frac{\langle \mathbf{u},\mathbf{v}\rangle}{\|\mathbf{u}\|_2\|\mathbf{v}\|_2}$ |
| Proyección sobre $\mathbf{a}$ | $\operatorname{proy}_{\mathbf{a}}(\mathbf{v}) = \frac{\langle \mathbf{v},\mathbf{a}\rangle}{\|\mathbf{a}\|^2} \mathbf{a}$ |
| Gram‑Schmidt | $\mathbf{u}_i = \frac{\mathbf{v}_i - \sum_{j<i}\langle \mathbf{v}_i,\mathbf{u}_j\rangle\mathbf{u}_j}{\|\dots\|}$ |








## Módulo 8: Espacios Vectoriales en Alta Dimensión y Aplicaciones Integradas

### 8.1 La maldición de la dimensionalidad

**Definición**: La “maldición de la dimensionalidad” (curse of dimensionality) es un conjunto de fenómenos que aparecen al trabajar en espacios de alta dimensión ($d$ grande). Contraintuitivamente, el volumen del espacio crece exponencialmente con $d$, lo que hace que los datos se vuelvan extremadamente esparcidos y que las distancias entre puntos pierdan su capacidad de discriminación.

**Crecimiento del volumen**: El volumen de una hiperesfera de radio $r$ en $\mathbb{R}^d$ es $V_d(r) = \frac{\pi^{d/2}}{\Gamma(d/2+1)} r^d$. Para $r=1$, el volumen tiende a $0$ cuando $d$ crece (la mayor parte del volumen se concentra en la cáscara exterior). Más aún, el volumen de un hipercubo de lado $1$ es $1$, pero la mayor parte del volumen de una esfera inscrita se pierde. En términos prácticos: para mantener la misma densidad de muestras, la cantidad de datos necesaria crece exponencialmente con $d$.

**Concentración de la distancia**: En alta dimensión, para una distribución razonable (por ejemplo, puntos uniformes en el hipercubo $[0,1]^d$), la distancia euclidiana entre dos puntos tiende a ser casi constante. En concreto, la razón entre la distancia máxima y la mínima tiende a $1$ cuando $d \to \infty$. Esto significa que **todas las distancias se vuelven similares**, haciendo que algoritmos basados en distancia (como KNN) pierdan su capacidad de distinguir vecinos cercanos de lejanos.

**Ejemplo numérico**: En $\mathbb{R}^d$, si se toman dos puntos aleatorios uniformes en $[0,1]^d$, la distancia euclidiana esperada es $\sqrt{d/6}$ y su varianza decrece como $1/d$. Para $d=1000$, la mayoría de las distancias están alrededor de $\sqrt{1000/6} \approx 12.9$ con una desviación muy pequeña. Así, el vecino más cercano y el más lejano están casi a la misma distancia.

**Interpretación en IA**:  
- Los algoritmos que dependen de la noción de proximidad (KNN, clustering, búsqueda por similitud) sufren mucho en alta dimensión a menos que se reduzca la dimensionalidad o se usen métricas alternativas (por ejemplo, distancia coseno o Manhattan).  
- Las redes neuronales profundas evitan parcialmente la maldición porque aprenden representaciones internas de baja dimensión (subespacios) donde los datos sí son densos.

---

### 8.2 Consecuencias prácticas en IA

#### 🔹 KNN en alta dimensión
El clasificador de k‑vecinos más cercanos compara el punto de prueba con todos los puntos de entrenamiento usando una distancia. Cuando $d$ es grande (por ejemplo, imágenes de $32\times32$ píxeles → $d=1024$), se necesitan exponencialmente más muestras para tener una densidad razonable. Con conjuntos de tamaño finito, el vecino más cercano puede estar lejísimos y la clasificación se vuelve poco mejor que aleatoria. Por ello, antes de aplicar KNN se suele reducir la dimensión (PCA, autoencoders) o se emplean distancias más robustas como la L1 o la coseno.

#### 🔹 Embeddings (word2vec, BERT, etc.)
Los embeddings de palabras o frases suelen tener dimensiones entre $50$ y $768$. Esta elección es un equilibrio:
- Dimensión demasiado baja → no se pueden capturar todas las relaciones semánticas (pérdida de expresividad).
- Dimensión demasiado alta → maldición de la dimensionalidad, sobreajuste y mayor coste computacional.
Los valores típicos (300 para word2vec, 768 para BERT base) se han determinado empíricamente como un punto óptimo.

#### 🔹 Bases de datos vectoriales
Almacenan millones de vectores de embedding (por ejemplo, para búsqueda semántica en documentos). La búsqueda exacta del vecino más cercano (distancia L2 o coseno) en $d=768$ sería $O(Nd)$, inviable para $N$ grande. Por ello se utilizan índices aproximados:
- **HNSW** (Hierarchical Navigable Small World): grafo jerárquico que permite búsqueda logarítmica.
- **IVF** (Inverted File Index): cuantización vectorial para reducir el espacio de búsqueda.
Estos métodos sacrifican exactitud por velocidad, asumiendo que la maldición hace que la distancia exacta no sea críticamente más informativa que una aproximación.

---

### 8.3 Aplicaciones integradas

#### 🔹 Embeddings vectoriales

**Word2Vec / GloVe / FastText**: Cada palabra se representa como un vector en $\mathbb{R}^d$ ($d$ típicamente 300). La propiedad clave es que las relaciones semánticas se codifican como operaciones vectoriales lineales:
$$ \text{rey} - \text{hombre} + \text{mujer} \approx \text{reina} $$
La similitud coseno mide la cercanía semántica: $\cos(\theta) = \frac{\langle \mathbf{u}, \mathbf{v} \rangle}{\|\mathbf{u}\|_2 \|\mathbf{v}\|_2}$. Dos palabras con significado similar tienen ángulo pequeño (coseno cercano a 1).

**Sentence embeddings (SBERT)**: Transforman frases completas en un único vector de $d=384$ o $768$. Se usan para búsqueda semántica: dada una consulta, se calcula su embedding y se busca en una base de datos vectorial los documentos con embedding más cercano (por coseno). Esto permite responder preguntas sobre grandes corpus sin necesidad de coincidencia exacta de palabras.

**Embeddings de imágenes**: Redes CNN (ResNet, EfficientNet) extraen vectores de características de imágenes. Por ejemplo, la capa justo antes de la clasificación produce un embedding de $d=2048$ que resume el contenido visual. Dos imágenes similares (mismo objeto, misma escena) tendrán embeddings con alta similitud coseno. Esto permite búsqueda de imágenes por contenido, recomendación de productos visualmente parecidos, etc.

---

#### 🔹 Regularización vía normas (aplicación en alta dimensión)

En modelos con muchas características (alta $d$), la regularización es crucial para evitar sobreajuste.

- **Regularización L2 (Ridge)**: Penaliza $\|\mathbf{w}\|_2^2$. Hace que todos los pesos sean pequeños pero ninguno exactamente cero. Útil cuando se cree que muchas características contribuyen débilmente.
- **Regularización L1 (Lasso)**: Penaliza $\|\mathbf{w}\|_1$. Produce **sparsity**: muchos pesos se vuelven exactamente cero, realizando selección de características. Ideal cuando se tienen cientos o miles de características, muchas de las cuales son irrelevantes.

**Interpretación geométrica en alta dimensión**: La bola L1 tiene “picos” en las direcciones de los ejes. Al minimizar el error empírico con restricción $\|\mathbf{w}\|_1 \le t$, la solución tiende a apoyarse en esos picos, anulando muchas componentes. En alta dimensión, el efecto sparse es especialmente valioso porque reduce el número efectivo de características, mitigando la maldición.

---

#### 🔹 SVM con kernels

El SVM lineal funciona bien si los datos son linealmente separables. Cuando no lo son, se aplica el **truco del kernel**: se mapean los datos a un espacio de características de mayor dimensión (incluso infinita) mediante una función $\phi: \mathbb{R}^n \to \mathcal{H}$, donde $\mathcal{H}$ es un espacio de Hilbert (espacio vectorial con producto interno). El kernel $K(\mathbf{x}, \mathbf{y}) = \langle \phi(\mathbf{x}), \phi(\mathbf{y}) \rangle_{\mathcal{H}}$ permite calcular el producto interno en $\mathcal{H}$ sin necesidad de conocer explícitamente $\phi$.

**Kernel RBF (gaussiano)**: $K(\mathbf{x}, \mathbf{y}) = \exp\left(-\gamma \|\mathbf{x} - \mathbf{y}\|^2\right)$. Este kernel corresponde a un espacio de características de dimensión infinita. En ese espacio, cualquier conjunto de datos con etiquetas diferentes se vuelve linealmente separable (teorema de Cover). La ortogonalidad en $\mathcal{H}$ permite encontrar un hiperplano separador que en el espacio original es una frontera no lineal (por ejemplo, circunferencias, elipses).

**Ventaja**: El kernel evita la maldición de la dimensionalidad porque el mapeo $\phi$ nunca se calcula explícitamente; todas las operaciones se realizan mediante la matriz de Gram $K_{ij} = K(\mathbf{x}_i, \mathbf{x}_j)$. Sin embargo, el número de puntos de entrenamiento $N$ sigue siendo un factor limitante (complejidad $O(N^3)$ para SVM con kernel).

---

#### 🔹 Generative AI (espacios latentes)

Los modelos generativos modernos (VAE, GAN, difusión) aprenden un mapeo desde un **espacio latente** $\mathcal{Z} = \mathbb{R}^d$ (con $d$ pequeño, típicamente $100$ a $512$) hacia el espacio de datos $\mathcal{X}$ (imágenes de alta dimensión, texto, audio). Este espacio latente es un subespacio (o variedad) donde los atributos semánticos están desenredados.

**Interpolación**: Dados dos puntos latentes $\mathbf{z}_1$ y $\mathbf{z}_2$, se define una trayectoria mediante combinación convexa:
$$ \mathbf{z}(t) = (1-t)\mathbf{z}_1 + t\mathbf{z}_2, \quad t \in [0,1] $$
Al pasar cada $\mathbf{z}(t)$ por el generador $G$, se obtiene una secuencia de imágenes que transicionan suavemente entre el contenido de $\mathbf{z}_1$ y $\mathbf{z}_2$. Por ejemplo, interpolando entre un “gato” y un “perro” se obtienen híbridos realistas. Esto funciona porque el generador es una función continua y el espacio latente es vectorial.

**Edición de atributos**: En espacios latentes bien estructurados (por ejemplo, StyleGAN), existe una dirección $\mathbf{d}$ tal que mover el vector latente como $\mathbf{z} + \alpha \mathbf{d}$ modifica un atributo específico (sonrisa, edad, color de pelo) sin alterar otros. Matemáticamente, $\mathbf{d}$ es un vector en el espacio latente que, al sumarse, produce un cambio controlado en la salida. Estas direcciones se pueden encontrar mediante álgebra lineal (por ejemplo, PCA sobre diferencias de pares de imágenes con y sin el atributo).

**Relación con espacios vectoriales**: El espacio latente es un espacio vectorial real de baja dimensión. Todas las operaciones lineales (suma, escalado, combinaciones convexas) tienen un significado semántico en la salida generada. Esto es una manifestación directa de la estructura de espacio vectorial en IA generativa.

---

#### 🔹 Bases de datos vectoriales (concepto)

Una **base de datos vectorial** es un sistema diseñado para almacenar y buscar vectores de alta dimensión (embeddings) de manera eficiente. Las operaciones típicas son:
- **Inserción**: guardar un vector junto con metadatos (por ejemplo, el texto original, la imagen).
- **Búsqueda por similitud**: dado un vector de consulta $\mathbf{q}$, devolver los $k$ vectores más cercanos según una distancia (L2, coseno, producto interno).

**Aplicaciones**:
- **Búsqueda semántica**: En RAG (Retrieval-Augmented Generation), se convierte una pregunta en un embedding, se buscan los documentos más relevantes en la base de datos vectorial, y se concatenan con la pregunta para que un LLM genere una respuesta informada.
- **Recomendación**: Usuarios y productos se representan como embeddings; recomendar un producto es buscar los embeddings de productos más cercanos al embedding del usuario.
- **Clasificación few‑shot**: Almacenar ejemplos etiquetados como vectores; clasificar un nuevo punto por mayoría entre sus vecinos vectoriales.

**Desafío**: La búsqueda exacta (vecino más cercano) en alta dimensión es costosa $O(Nd)$. Por eso las bases de datos vectoriales utilizan índices aproximados (HNSW, IVF, PQ) que reducen la complejidad a $O(\log N)$ o $O(1)$ con pequeña pérdida de precisión. Esto es posible porque, debido a la maldición de la dimensionalidad, la diferencia entre el vecino exacto y uno aproximado es a menudo pequeña.

---

### 8.4 Tabla resumen de aplicaciones en alta dimensión

| Aplicación | Dimensión típica | Operación vectorial clave | Cómo mitiga la maldición |
|------------|------------------|---------------------------|---------------------------|
| Word2Vec embeddings | 300 | Similitud coseno | Dimensión fija moderada; usa ángulo, no distancia L2 |
| BERT embeddings | 768 | Producto interno (atención) | Índices aproximados (HNSW) para búsqueda |
| KNN en imágenes | > 1000 | Distancia L2 / L1 | Se reduce dimensión previamente (PCA, autoencoder) |
| SVM con kernel RBF | Infinita | Kernel (producto interno implícito) | No se calcula $\phi$ explícitamente; usa matriz de Gram |
| Espacios latentes (GAN) | 100–512 | Combinación convexa, suma de vectores | Baja dimensión por diseño (subespacio) |
| Bases de datos vectoriales | 128–2048 | Distancia coseno / L2 | Índices aproximados (HNSW, IVF) |

---






## Resumen de conexiones (tabla para repaso rápido)

| Concepto matemático | Aplicación en IA |
|---------------------|------------------|
| Espacio vectorial | Representación de datos (features, embeddings, pesos) |
| Subespacio | Espacio latente en autoencoders / GenAI |
| Independencia lineal | Detección de features redundantes |
| Cambio de base | Kernels (mapeo implícito a otro espacio) |
| Norma L1 / L2 / L∞ | Regularización (Lasso, Ridge), bolas unitarias |
| Distancia L1, L2, coseno | KNN, búsqueda de vecinos, similaridad de embeddings |
| Producto interno | Atención (Attention), similitud coseno, SVM lineal |
| Proyección ortogonal | Regresión lineal (mínimos cuadrados), eliminación de ruido |
| Bola unitaria | Región factible para pesos en regularización |
| Alta dimensionalidad | Maldición, embeddings, bases de datos vectoriales |