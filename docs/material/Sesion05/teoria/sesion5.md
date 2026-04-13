---
layout: default
---
# Sesión 5: Espacios Vectoriales y Normas

### Teoría

#### 1. Espacio vectorial ℝⁿ, subespacios

Un **espacio vectorial** es un conjunto de vectores que es cerrado bajo dos operaciones: suma de vectores y multiplicación por un escalar, cumpliendo ciertas propiedades (asociatividad, conmutatividad, existencia de elemento neutro, etc.).

El espacio ℝⁿ es el conjunto de todos los vectores de $n$ componentes reales:

$$
\mathbb{R}^n = \{ \mathbf{x} = (x_1, x_2, \dots, x_n) \mid x_i \in \mathbb{R} \}
$$

**Ejemplos:**
- ℝ¹: la recta real.
- ℝ²: el plano cartesiano.
- ℝ³: el espacio tridimensional.

**Subespacio vectorial:** Un subconjunto $S \subseteq \mathbb{R}^n$ que es en sí mismo un espacio vectorial (cerrado bajo suma y multiplicación por escalar).

**Ejemplos de subespacios en ℝ³:**
- El origen $\{ (0,0,0) \}$.
- Rectas que pasan por el origen.
- Planos que pasan por el origen.
- Todo ℝ³.

**No son subespacios:** Rectas o planos que no pasan por el origen.

#### 2. Combinación lineal, independencia lineal, bases, dimensión, cambio de base

**Combinación lineal:** Dados vectores $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k \in \mathbb{R}^n$ y escalares $\alpha_1, \alpha_2, \dots, \alpha_k \in \mathbb{R}$, la combinación lineal es:

$$
\alpha_1 \mathbf{v}_1 + \alpha_2 \mathbf{v}_2 + \cdots + \alpha_k \mathbf{v}_k
$$

**Ejemplo:** En ℝ², $\mathbf{v}_1 = (1,0)$, $\mathbf{v}_2 = (0,1)$, una combinación lineal $3\mathbf{v}_1 + 2\mathbf{v}_2 = (3,2)$.

**Independencia lineal:** Un conjunto de vectores es linealmente independiente si la única combinación lineal que da el vector cero es aquella con todos los coeficientes cero:

$$
\alpha_1 \mathbf{v}_1 + \cdots + \alpha_k \mathbf{v}_k = \mathbf{0} \quad \Rightarrow \quad \alpha_1 = \cdots = \alpha_k = 0
$$

**Ejemplo:** $\mathbf{v}_1 = (1,0)$, $\mathbf{v}_2 = (0,1)$ son independientes.  
$\mathbf{v}_1 = (1,2)$, $\mathbf{v}_2 = (2,4)$ son dependientes (porque $\mathbf{v}_2 = 2\mathbf{v}_1$).

**Base:** Un conjunto de vectores linealmente independientes que genera todo el espacio. En ℝⁿ, la base canónica es:

$$
\mathbf{e}_1 = (1,0,\dots,0),\quad \mathbf{e}_2 = (0,1,\dots,0),\quad \dots,\quad \mathbf{e}_n = (0,0,\dots,1)
$$

**Dimensión:** El número de vectores en cualquier base de un espacio vectorial. ℝⁿ tiene dimensión $n$.

**Cambio de base:** Si tenemos dos bases $B = \{\mathbf{v}_1,\dots,\mathbf{v}_n\}$ y $B' = \{\mathbf{w}_1,\dots,\mathbf{w}_n\}$, existe una matriz de cambio de base $P$ tal que las coordenadas de un vector en base $B'$ se obtienen multiplicando $P$ por las coordenadas en base $B$.

**Ejemplo:** En ℝ², sea base canónica $B = \{(1,0), (0,1)\}$ y otra base $B' = \{(1,1), (1,-1)\}$. Un vector $\mathbf{x} = (3,2)$ en base canónica tiene coordenadas $(3,2)$. Para expresarlo en base $B'$, resolvemos:

$$
(3,2) = \alpha(1,1) + \beta(1,-1) = (\alpha+\beta,\; \alpha-\beta)
$$
$$
\begin{cases}
\alpha + \beta = 3 \\
\alpha - \beta = 2
\end{cases}
\Rightarrow \alpha = 2.5,\; \beta = 0.5
$$

Así, las coordenadas en base $B'$ son $(2.5, 0.5)$.

#### 3. Producto punto, ángulo entre vectores, similitud coseno

**Producto punto (escalar):** Para vectores $\mathbf{u} = (u_1, u_2, \dots, u_n)$ y $\mathbf{v} = (v_1, v_2, \dots, v_n)$:

$$
\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^{n} u_i v_i = u_1 v_1 + u_2 v_2 + \cdots + u_n v_n
$$

**Ejemplo:** $\mathbf{u} = (2, -1, 3)$, $\mathbf{v} = (1, 0, 4)$  
$\mathbf{u} \cdot \mathbf{v} = 2\cdot1 + (-1)\cdot0 + 3\cdot4 = 2 + 0 + 12 = 14$

**Norma (longitud) de un vector:** $\|\mathbf{v}\| = \sqrt{\mathbf{v} \cdot \mathbf{v}}$

**Ejemplo:** $\|\mathbf{u}\| = \sqrt{2^2 + (-1)^2 + 3^2} = \sqrt{4 + 1 + 9} = \sqrt{14} \approx 3.74$

**Ángulo entre vectores:** El coseno del ángulo $\theta$ entre $\mathbf{u}$ y $\mathbf{v}$ es:

$$
\cos \theta = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{u}\| \|\mathbf{v}\|}
$$

**Ejemplo:** Con $\mathbf{u}$ y $\mathbf{v}$ anteriores:
$$
\cos \theta = \frac{14}{\sqrt{14} \cdot \sqrt{1^2+0^2+4^2}} = \frac{14}{\sqrt{14} \cdot \sqrt{17}} = \frac{14}{\sqrt{238}} \approx \frac{14}{15.43} \approx 0.907
$$
$\theta \approx \arccos(0.907) \approx 24.9°$

**Similitud coseno:** Es exactamente $\cos \theta$, usada para medir similitud entre vectores (especialmente cuando la magnitud no es relevante). Valores cercanos a 1 indican vectores similares (misma dirección), cercanos a -1 indican direcciones opuestas, cercanos a 0 indican ortogonalidad.

#### 4. Normas: L1, L2, L∞; interpretación geométrica

Una **norma** es una función que asigna un número real no negativo a cada vector, cumpliendo ciertas propiedades (homogeneidad, desigualdad triangular, etc.). Las normas más comunes son:

**Norma L2 (euclidiana):** La longitud estándar.
$$
\|\mathbf{x}\|_2 = \sqrt{\sum_{i=1}^{n} x_i^2}
$$

**Norma L1 (Manhattan):** Suma de valores absolutos.
$$
\|\mathbf{x}\|_1 = \sum_{i=1}^{n} |x_i|
$$

**Norma L∞ (máximo):** El valor absoluto máximo.
$$
\|\mathbf{x}\|_\infty = \max_{i} |x_i|
$$

**Ejemplo:** Para $\mathbf{x} = (3, -4, 2)$:
- $\|\mathbf{x}\|_2 = \sqrt{3^2 + (-4)^2 + 2^2} = \sqrt{9 + 16 + 4} = \sqrt{29} \approx 5.385$
- $\|\mathbf{x}\|_1 = |3| + |-4| + |2| = 3 + 4 + 2 = 9$
- $\|\mathbf{x}\|_\infty = \max(3, 4, 2) = 4$

**Interpretación geométrica:**

- **L2:** Distancia en línea recta (como el teorema de Pitágoras).
- **L1:** Distancia recorrida en una cuadrícula (como caminar por calles de Manhattan).
- **L∞:** Distancia máxima en cualquier coordenada (como mover un rey en ajedrez).

#### 5. Distancias: euclidiana, Manhattan, Chebyshev; bola unitaria

Una **distancia** entre dos vectores $\mathbf{x}$ e $\mathbf{y}$ se define generalmente como la norma de su diferencia:

$$
d(\mathbf{x}, \mathbf{y}) = \|\mathbf{x} - \mathbf{y}\|
$$

- **Distancia euclidiana:** $d_2(\mathbf{x}, \mathbf{y}) = \|\mathbf{x} - \mathbf{y}\|_2$
- **Distancia Manhattan:** $d_1(\mathbf{x}, \mathbf{y}) = \|\mathbf{x} - \mathbf{y}\|_1$
- **Distancia Chebyshev:** $d_\infty(\mathbf{x}, \mathbf{y}) = \|\mathbf{x} - \mathbf{y}\|_\infty$

**Ejemplo:** $\mathbf{x} = (1,2)$, $\mathbf{y} = (4,6)$:
- $d_2 = \sqrt{(1-4)^2 + (2-6)^2} = \sqrt{9 + 16} = \sqrt{25} = 5$
- $d_1 = |1-4| + |2-6| = 3 + 4 = 7$
- $d_\infty = \max(|1-4|, |2-6|) = \max(3, 4) = 4$

**Bola unitaria:** Conjunto de vectores con norma ≤ 1. La forma de la bola depende de la norma:
- L2: círculo (en ℝ²) o esfera (en ℝ³).
- L1: diamante (rombo).
- L∞: cuadrado.

#### 6. Proyecciones ortogonales

La proyección ortogonal de un vector $\mathbf{u}$ sobre un vector $\mathbf{v}$ es:

$$
\text{proy}_{\mathbf{v}}(\mathbf{u}) = \frac{\mathbf{u} \cdot \mathbf{v}}{\mathbf{v} \cdot \mathbf{v}} \mathbf{v}
$$

**Ejemplo:** $\mathbf{u} = (3,4)$, $\mathbf{v} = (1,2)$:
$$
\frac{\mathbf{u} \cdot \mathbf{v}}{\mathbf{v} \cdot \mathbf{v}} = \frac{3\cdot1 + 4\cdot2}{1^2 + 2^2} = \frac{3+8}{1+4} = \frac{11}{5} = 2.2
$$
$$
\text{proy}_{\mathbf{v}}(\mathbf{u}) = 2.2 \cdot (1,2) = (2.2, 4.4)
$$

La proyección sobre un subespacio (ej. un plano) generaliza esta idea.

#### 7. Rectas, planos e hiperplanos; semiespacios

**Recta en ℝⁿ:** Puede describirse paramétricamente como $\mathbf{x} = \mathbf{p} + t\mathbf{d}$, donde $\mathbf{p}$ es un punto y $\mathbf{d}$ es un vector dirección.

**Plano en ℝ³:** $\mathbf{n} \cdot (\mathbf{x} - \mathbf{p}) = 0$, donde $\mathbf{n}$ es un vector normal.

**Hiperplano en ℝⁿ:** Generalización: $\mathbf{n} \cdot \mathbf{x} = c$, con $\mathbf{n} \in \mathbb{R}^n$ (vector normal) y $c \in \mathbb{R}$.

**Semiespacio:** Región a un lado de un hiperplano: $\mathbf{n} \cdot \mathbf{x} \leq c$ o $\mathbf{n} \cdot \mathbf{x} \geq c$.

#### 8. Concepto de regularización basada en normas

En machine learning, a menudo añadimos un término de regularización a la función de pérdida para controlar la complejidad del modelo y evitar overfitting. La regularización basada en normas penaliza los parámetros grandes:

$$
L_{\text{reg}}(\theta) = L(\theta) + \lambda \|\theta\|_p
$$

- **Regularización L2 (Ridge):** Usa $\|\theta\|_2^2$. Penaliza pesos grandes, tendiendo a distribuirlos uniformemente.
- **Regularización L1 (Lasso):** Usa $\|\theta\|_1$. Tiende a producir soluciones dispersas (muchos pesos exactamente cero).

La elección de la norma tiene un efecto geométrico en la región factible y en la solución.

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. Regularización Ridge (L2) y Lasso (L1)

En regresión lineal, la función de costo con regularización es:

- **Ridge (L2):** $L(\mathbf{w}) = \frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda \|\mathbf{w}\|_2^2$
- **Lasso (L1):** $L(\mathbf{w}) = \frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda \|\mathbf{w}\|_1$

**Ejemplo Ridge con una variable:**  
Datos: (1,2), (2,3), (3,5). Sin regularización, encontramos $w = 1.5, b = 0.333$.  
Con Ridge, la solución minimiza $ \sum (y_i - (wx_i+b))^2 + \lambda (w^2 + b^2)$. Para $\lambda = 0.1$, el nuevo $w$ será ligeramente menor.

**Efecto geométrico:** La regularización L2 restringe los pesos a una bola, L1 a un diamante. L1 tiende a dar soluciones en los vértices (pesos cero).

##### 2. KNN (distancias)

K-Nearest Neighbors clasifica un punto basándose en los $k$ vecinos más cercanos según alguna distancia. Las distancias comunes son:

- Euclidiana (L2)
- Manhattan (L1)
- Chebyshev (L∞)

**Ejemplo:** Punto nuevo $\mathbf{x} = (2,3)$, vecinos conocidos:  
$\mathbf{x}_1 = (1,2)$ (clase A), $\mathbf{x}_2 = (3,4)$ (clase A), $\mathbf{x}_3 = (2,1)$ (clase B).  
Distancias euclidianas:  
$d(\mathbf{x},\mathbf{x}_1) = \sqrt{(2-1)^2 + (3-2)^2} = \sqrt{1+1} = \sqrt{2} \approx 1.41$  
$d(\mathbf{x},\mathbf{x}_2) = \sqrt{(2-3)^2 + (3-4)^2} = \sqrt{1+1} = 1.41$  
$d(\mathbf{x},\mathbf{x}_3) = \sqrt{(2-2)^2 + (3-1)^2} = \sqrt{0+4} = 2$  
Con $k=2$, los dos más cercanos son de clase A, así que se clasifica como A.

##### 3. SVM (producto punto, margen, normas)

Support Vector Machines busca un hiperplano que separe las clases con el máximo margen. La función de decisión es:

$$
f(\mathbf{x}) = \mathbf{w} \cdot \mathbf{x} + b
$$

El margen es $\frac{2}{\|\mathbf{w}\|}$. Maximizar el margen equivale a minimizar $\|\mathbf{w}\|^2$ sujeto a restricciones de clasificación correcta.

El producto punto aparece en la función de decisión y en el cálculo del kernel (ej. kernel lineal: $K(\mathbf{x},\mathbf{x}') = \mathbf{x} \cdot \mathbf{x}'$).

**Ejemplo:** En 2D, un SVM lineal con vectores de soporte encuentra $\mathbf{w}$ y $b$ tales que $\mathbf{w} \cdot \mathbf{x}_i + b \geq 1$ para clase positiva y $\leq -1$ para negativa.

##### 4. Clustering (distancias, silhouette)

En K-Means, la asignación de puntos a clusters se basa en la distancia al centroide (normalmente euclidiana). La pérdida es la suma de distancias al cuadrado (norma L2).

El coeficiente de **silhouette** mide qué tan bien separados están los clusters:

$$
s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}
$$
donde $a(i)$ es la distancia promedio de $i$ a otros puntos de su cluster, y $b(i)$ es la distancia promedio al cluster vecino más cercano. Aquí se usan distancias (generalmente euclidianas).

##### 5. Sistemas de recomendación (similitud coseno)

En filtrado colaborativo basado en ítems, se recomiendan ítems similares a los que el usuario ha valorado positivamente. La similitud entre ítems se mide frecuentemente con el **coseno** de los vectores de valoraciones:

$$
\text{sim}(i,j) = \frac{\mathbf{r}_i \cdot \mathbf{r}_j}{\|\mathbf{r}_i\| \|\mathbf{r}_j\|}
$$

**Ejemplo:** Ítem 1: valoraciones de 3 usuarios (5, 3, 0). Ítem 2: (4, 3, 0).  
Producto punto: $5\cdot4 + 3\cdot3 + 0\cdot0 = 20 + 9 = 29$  
Normas: $\sqrt{25+9+0} = \sqrt{34} \approx 5.83$, $\sqrt{16+9+0} = \sqrt{25} = 5$  
Similitud = $29 / (5.83 \times 5) \approx 29 / 29.15 \approx 0.995$ (muy similares).

##### 6. Huber loss

La función de pérdida de Huber combina MSE y MAE para ser robusta a outliers:

$$
L_\delta(y, \hat{y}) = 
\begin{cases}
\frac{1}{2}(y - \hat{y})^2 & \text{si } |y - \hat{y}| \leq \delta \\
\delta |y - \hat{y}| - \frac{1}{2}\delta^2 & \text{en otro caso}
\end{cases}
$$

Aquí, la distancia (error) se mide en valor absoluto para outliers, y cuadrática para errores pequeños. Es una mezcla de normas L2 y L1.

#### Deep Learning (DL)

##### 1. Regularización en redes (normas de pesos)

En redes neuronales, es común aplicar **weight decay** (regularización L2) en los pesos:

$$
L_{\text{total}} = L_{\text{original}} + \lambda \sum_{l} \|W^{(l)}\|_F^2
$$
donde $\|W\|_F$ es la norma de Frobenius (equivalente a L2 para matrices). Esto ayuda a prevenir overfitting.

##### 2. LoRA (normas de matrices)

LoRA (Low-Rank Adaptation) es una técnica para fine-tuning eficiente de modelos grandes. Se basa en descomponer la actualización de pesos como producto de matrices de bajo rango:

$$
W = W_0 + BA
$$
donde $B \in \mathbb{R}^{d \times r}$, $A \in \mathbb{R}^{r \times k}$ con $r \ll \min(d,k)$. La norma de Frobenius de estas matrices se controla implícitamente al limitar el rango.

##### 3. Atención (producto punto Q·K)

En el mecanismo de atención, la compatibilidad entre un query y un key se calcula con producto punto (o versión escalada):

$$
\text{score}(\mathbf{q}, \mathbf{k}) = \mathbf{q} \cdot \mathbf{k}
$$

Luego, estos scores se normalizan con softmax. La atención multi-cabeza realiza múltiples productos punto en paralelo.

**Ejemplo:** En un transformer, para una secuencia, las matrices Q, K, V se multiplican: $\text{Attention}(Q,K,V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$. El producto $QK^T$ contiene todos los productos punto entre queries y keys.

##### 4. RAG (búsqueda de vecinos, distancias)

Retrieval-Augmented Generation combina un recuperador con un generador. El recuperador encuentra documentos relevantes para una consulta usando **búsqueda de vecinos más cercanos** en un espacio de embeddings. Las distancias comunes son euclidiana o coseno.

**Ejemplo:** La consulta se convierte en un embedding $\mathbf{q}$. Se buscan en una base vectorial (FAISS) los $k$ vectores de documentos con menor distancia euclidiana o mayor similitud coseno.

##### 5. CLIP (similitud coseno)

CLIP (Contrastive Language-Image Pre-training) aprende un espacio de embeddings conjunto para imágenes y textos. Durante el entrenamiento, se maximiza la similitud coseno entre pares imagen-texto correctos y se minimiza para pares incorrectos.

La pérdida contrastiva usa:

$$
\text{sim}(I,T) = \frac{\mathbf{v}_I \cdot \mathbf{v}_T}{\|\mathbf{v}_I\| \|\mathbf{v}_T\|}
$$

**Ejemplo:** Para un batch de $N$ pares, se forma una matriz $N \times N$ de similitudes coseno. Se aplica softmax por filas y se usa cross-entropy para que los elementos diagonales (pares correctos) tengan alta probabilidad.

---

