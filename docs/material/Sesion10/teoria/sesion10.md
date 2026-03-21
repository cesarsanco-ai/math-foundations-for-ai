## Semana 10: Probabilidad y Estadística para IA

### Teoría

#### 1. Probabilidad básica

##### Axiomas de probabilidad

La probabilidad es una medida que cuantifica la incertidumbre. Para un espacio muestral \(\Omega\) (conjunto de todos los resultados posibles), una probabilidad \(P\) asigna a cada evento \(A \subseteq \Omega\) un número real que satisface:

1. **No negatividad:** \(P(A) \geq 0\) para todo evento \(A\).
2. **Normalización:** \(P(\Omega) = 1\).
3. **Aditividad:** Si \(A\) y \(B\) son eventos mutuamente excluyentes (\(A \cap B = \emptyset\)), entonces \(P(A \cup B) = P(A) + P(B)\).

**Ejemplo:** Lanzar un dado justo: \(\Omega = \{1,2,3,4,5,6\}\). \(P(\{2\}) = 1/6\). \(P(\{2,4,6\}) = 3/6 = 0.5\).

##### Probabilidad condicional

La probabilidad de que ocurra \(A\) dado que ocurrió \(B\) se define como:

\[
P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad \text{si } P(B) > 0
\]

**Ejemplo:** En una baraja de 52 cartas, sea \(A\) = "sacar un as" y \(B\) = "sacar una carta roja". Hay 2 ases rojos (corazones y diamantes). \(P(A \cap B) = 2/52 = 1/26\). \(P(B) = 26/52 = 1/2\). Entonces \(P(A|B) = (1/26)/(1/2) = (1/26) \times 2 = 2/26 = 1/13 \approx 0.077\).

##### Independencia

Dos eventos \(A\) y \(B\) son independientes si:

\[
P(A \cap B) = P(A) P(B)
\]
o equivalentemente, \(P(A|B) = P(A)\).

**Ejemplo:** Lanzar dos monedas. \(A\) = "primera moneda sale cara", \(B\) = "segunda moneda sale cara". \(P(A)=0.5\), \(P(B)=0.5\), \(P(A \cap B)=0.25\). Como \(0.25 = 0.5 \times 0.5\), son independientes.

##### Teorema de Bayes

Relaciona probabilidades condicionales:

\[
P(A|B) = \frac{P(B|A) P(A)}{P(B)}
\]

Es fundamental en inferencia estadística y aprendizaje automático, ya que permite actualizar creencias a partir de evidencia.

**Ejemplo:** Una prueba para detectar una enfermedad tiene 99% de sensibilidad (detecta correctamente a enfermos) y 98% de especificidad (detecta correctamente a sanos). La enfermedad afecta al 1% de la población. Si una persona da positivo, ¿cuál es la probabilidad de que realmente esté enferma?

- \(A\) = "tener la enfermedad", \(P(A) = 0.01\)
- \(B\) = "dar positivo"
- \(P(B|A) = 0.99\) (sensibilidad)
- \(P(B|A^c) = 1 - 0.98 = 0.02\) (tasa de falsos positivos)

Calculamos \(P(B) = P(B|A)P(A) + P(B|A^c)P(A^c) = 0.99 \times 0.01 + 0.02 \times 0.99 = 0.0099 + 0.0198 = 0.0297\)

Aplicamos Bayes:

\[
P(A|B) = \frac{0.99 \times 0.01}{0.0297} = \frac{0.0099}{0.0297} = 0.3333...
\]

¡Solo 33%! A pesar de la alta precisión de la prueba, la baja prevalencia hace que la mayoría de los positivos sean falsos.

#### 2. Variables aleatorias, esperanza, varianza, covarianza

##### Variable aleatoria

Una variable aleatoria es una función que asigna un valor numérico a cada resultado del espacio muestral. Puede ser:

- **Discreta:** Toma valores en un conjunto finito o numerable (ej. número de caras al lanzar 3 monedas).
- **Continua:** Toma valores en un intervalo real (ej. altura de una persona).

**Ejemplo:** Lanzar dos dados y sumar sus valores. La suma es una variable aleatoria discreta que puede tomar valores de 2 a 12.

##### Esperanza (media)

La esperanza matemática \(E[X]\) es el valor promedio ponderado de una variable aleatoria.

- Para variable discreta: \(E[X] = \sum_i x_i P(X = x_i)\)
- Para variable continua: \(E[X] = \int x f(x) dx\), donde \(f\) es la función de densidad.

**Ejemplo:** Lanzar un dado justo: \(E[X] = 1\cdot\frac{1}{6} + 2\cdot\frac{1}{6} + \cdots + 6\cdot\frac{1}{6} = \frac{21}{6} = 3.5\)

##### Varianza

Mide la dispersión de los valores alrededor de la media:

\[
\text{Var}(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2
\]

La desviación estándar es \(\sigma_X = \sqrt{\text{Var}(X)}\).

**Ejemplo:** Para el dado: \(E[X^2] = 1^2\cdot\frac{1}{6} + 2^2\cdot\frac{1}{6} + \cdots + 6^2\cdot\frac{1}{6} = \frac{91}{6} \approx 15.167\). Entonces \(\text{Var}(X) = 15.167 - 3.5^2 = 15.167 - 12.25 = 2.917\), \(\sigma_X \approx 1.708\).

##### Covarianza

Mide la relación lineal entre dos variables aleatorias:

\[
\text{Cov}(X, Y) = E[(X - E[X])(Y - E[Y])] = E[XY] - E[X]E[Y]
\]

- Si es positiva: tienden a moverse en la misma dirección.
- Si es negativa: tienden a moverse en direcciones opuestas.
- Si es cero: no hay relación lineal (aunque podría haber otra relación).

**Ejemplo:** Sean \(X\) = altura, \(Y\) = peso. Generalmente covarianza positiva (a mayor altura, mayor peso en promedio).

La **correlación** (Pearson) normaliza la covarianza:

\[
\rho_{XY} = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y} \in [-1, 1]
\]

#### 3. Distribuciones

##### Distribución normal (Gaussiana)

Es la distribución continua más importante. Su función de densidad es:

\[
f(x|\mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
\]

donde \(\mu\) es la media y \(\sigma^2\) la varianza. La normal estándar tiene \(\mu=0\), \(\sigma=1\).

**Propiedad:** Por el Teorema Central del Límite, la suma de muchas variables independientes tiende a una normal.

**Ejemplo:** Alturas de una población, errores de medición.

##### Distribución de Bernoulli

Modela un experimento con dos resultados (éxito/fracaso). \(X \sim \text{Bernoulli}(p)\):

- \(P(X=1) = p\) (éxito)
- \(P(X=0) = 1-p\) (fracaso)

**Esperanza:** \(E[X] = p\)  
**Varianza:** \(\text{Var}(X) = p(1-p)\)

**Ejemplo:** Lanzar una moneda: \(p=0.5\).

##### Distribución multinomial

Generaliza la binomial a más de dos categorías. Modela el número de veces que ocurre cada categoría en \(n\) ensayos independientes, con probabilidades \(p_1, p_2, \dots, p_k\) que suman 1.

**Ejemplo:** Lanzar un dado 10 veces y contar cuántas veces sale cada cara.

##### Distribución uniforme

- **Uniforme discreta:** Todos los resultados tienen igual probabilidad. Ejemplo: dado justo.
- **Uniforme continua:** Densidad constante en un intervalo \([a, b]\): \(f(x) = \frac{1}{b-a}\) para \(x \in [a, b]\).

**Ejemplo:** Generar números aleatorios entre 0 y 1.

#### 4. Estadística descriptiva

##### Medidas de tendencia central

- **Media:** \(\bar{x} = \frac{1}{n}\sum_{i=1}^n x_i\)
- **Mediana:** Valor que divide la muestra en dos mitades (50% por debajo).
- **Moda:** Valor que más se repite.

**Ejemplo:** Datos: {2, 3, 3, 5, 7, 8, 10}. Media = (2+3+3+5+7+8+10)/7 = 38/7 ≈ 5.43. Mediana = 5 (el cuarto valor). Moda = 3.

##### Medidas de dispersión

- **Rango:** max - min.
- **Varianza muestral:** \(s^2 = \frac{1}{n-1}\sum (x_i - \bar{x})^2\)
- **Desviación estándar:** \(s = \sqrt{s^2}\)
- **Cuartiles:** Q1 (25%), Q2 (mediana, 50%), Q3 (75%). Rango intercuartil (IQR) = Q3 - Q1.

**Ejemplo:** Con los datos anteriores, Q1 = 3, Q3 = 8, IQR = 5.

##### Correlación

- **Pearson:** Mide relación lineal. Sensible a outliers.
- **Spearman:** Basado en rangos, mide cualquier relación monótona (no necesariamente lineal).

**Ejemplo:** Calcular Pearson para (x, y) = (1,2), (2,3), (3,5). Primero medias: \(\bar{x}=2\), \(\bar{y}=10/3≈3.33\). Covarianza = \(((1-2)(2-3.33)+(2-2)(3-3.33)+(3-2)(5-3.33))/2\) (usando n-1) = ((-1)(-1.33)+ (0)(-0.33)+ (1)(1.67))/2 = (1.33+0+1.67)/2 = 3/2 = 1.5. Desviaciones: \(s_x = \sqrt{((1-2)^2+(2-2)^2+(3-2)^2)/2} = \sqrt{(1+0+1)/2} = \sqrt{1} = 1\); \(s_y = \sqrt{((2-3.33)^2+(3-3.33)^2+(5-3.33)^2)/2} = \sqrt{(1.77+0.11+2.79)/2} = \sqrt{4.67/2} = \sqrt{2.335} ≈ 1.528\). Entonces \(r = 1.5 / (1 × 1.528) ≈ 0.982\).

#### 5. Entropía, información mutua, divergencia KL

##### Entropía (Shannon)

Mide la incertidumbre o sorpresa promedio de una variable aleatoria. Para una distribución discreta \(P\):

\[
H(P) = -\sum_{i} p_i \log_2 p_i \quad (\text{en bits}) \quad \text{o} \quad H(P) = -\sum_{i} p_i \ln p_i \quad (\text{en nats})
\]

**Propiedades:** La entropía es máxima cuando todos los eventos son equiprobables. Mínima (0) cuando un evento tiene probabilidad 1.

**Ejemplo:** Moneda justa: \(H = -0.5\log_2 0.5 - 0.5\log_2 0.5 = -0.5(-1) -0.5(-1) = 0.5+0.5 = 1\) bit. Moneda sesgada p=0.9: \(H = -0.9\log_2 0.9 - 0.1\log_2 0.1 \approx -0.9(-0.152) -0.1(-3.322) = 0.137 + 0.332 = 0.469\) bits (menos incertidumbre).

##### Información mutua

Mide la dependencia entre dos variables: cuánto reduce el conocimiento de una la incertidumbre de la otra.

\[
I(X;Y) = H(X) - H(X|Y) = \sum_{x,y} p(x,y) \log \frac{p(x,y)}{p(x)p(y)}
\]

Es cero si son independientes.

##### Divergencia KL (Kullback-Leibler)

Mide la "distancia" entre dos distribuciones \(P\) y \(Q\) (no es simétrica ni una métrica):

\[
D_{KL}(P \parallel Q) = \sum_i p_i \log \frac{p_i}{q_i}
\]

Interpretación: número promedio de bits adicionales necesarios para codificar muestras de \(P\) usando un código óptimo para \(Q\). En aprendizaje automático, minimizar la divergencia KL es equivalente a maximizar la verosimilitud.

**Ejemplo:** \(P = [0.5, 0.5]\), \(Q = [0.9, 0.1]\). \(D_{KL}(P||Q) = 0.5\log(0.5/0.9) + 0.5\log(0.5/0.1) = 0.5\log(0.556) + 0.5\log(5) ≈ 0.5(-0.847) + 0.5(2.302) = -0.4235 + 1.151 = 0.7275\) nats.

#### 6. Tests estadísticos

##### Test de Kolmogorov-Smirnov (KS)

Compara dos distribuciones (una muestra vs teórica, o dos muestras). Mide la máxima diferencia entre las funciones de distribución acumulada.

**Ejemplo:** En detección de data drift, comparamos la distribución de una característica en entrenamiento vs en producción. Si el estadístico KS es grande y el p-valor pequeño, hay drift.

##### PSI (Population Stability Index)

Mide el cambio en la distribución de una variable entre dos momentos. Común en monitoreo de modelos:

\[
\text{PSI} = \sum_{i} (\%\text{actual}_i - \%\text{esperado}_i) \cdot \ln\left(\frac{\%\text{actual}_i}{\%\text{esperado}_i}\right)
\]

Valores > 0.25 indican drift significativo.

##### p-valor

Probabilidad de obtener un resultado tan extremo como el observado, asumiendo que la hipótesis nula es cierta. Si p < 0.05 (típicamente), se rechaza la hipótesis nula.

##### Intervalos de confianza

Rango de valores que con cierta confianza (ej. 95%) contiene el verdadero parámetro poblacional. Para la media con varianza conocida:

\[
\bar{x} \pm z_{\alpha/2} \frac{\sigma}{\sqrt{n}}
\]

---

### Aplicaciones prácticas

#### Machine Learning (ML)

##### 1. EDA (estadística descriptiva)

El Análisis Exploratorio de Datos (EDA) utiliza todas las medidas descriptivas: media, mediana, desviación estándar, cuartiles para entender la distribución de cada característica; correlación para detectar relaciones lineales; histogramas y boxplots para visualizar.

**Ejemplo:** En un dataset de precios de viviendas, calculamos media = 250k, mediana = 200k (distribución sesgada). Desviación estándar = 100k indica mucha variabilidad. Correlación entre tamaño y precio = 0.85 (fuerte positiva).

##### 2. Regresión logística (probabilidad)

La regresión logística modela la probabilidad de pertenencia a una clase:

\[
P(y=1|x) = \sigma(w^T x + b) = \frac{1}{1 + e^{-(w^T x + b)}}
\]

Se entrena maximizando la verosimilitud (equivalente a minimizar cross-entropy). La salida es una probabilidad.

**Ejemplo:** Con w = [0.5, -0.3], b = 0.1, para x = [2, 1], z = 0.5×2 + (-0.3)×1 + 0.1 = 1 -0.3 +0.1 = 0.8, P = 1/(1+e^{-0.8}) ≈ 0.69.

##### 3. Naive Bayes (teorema de Bayes)

El clasificador Naive Bayes aplica el teorema de Bayes con el supuesto de independencia condicional entre características:

\[
P(y|x_1,\dots,x_n) \propto P(y) \prod_{i=1}^n P(x_i|y)
```

**Ejemplo:** Clasificación de correos spam/no spam. Para un correo con palabras "oferta" y "dinero", calculamos P(spam) * P("oferta"|spam) * P("dinero"|spam) y lo comparamos con P(no spam) * P("oferta"|no spam) * P("dinero"|no spam). La clase con mayor probabilidad es la predicción.

##### 4. Árboles de decisión (entropía, Gini)

Los árboles usan medidas de impureza para decidir splits:

- **Entropía:** \(H(S) = -\sum p_i \log_2 p_i\)
- **Índice Gini:** \(G(S) = 1 - \sum p_i^2\)

**Ejemplo:** Un nodo con 10 muestras: 6 de clase A, 4 de clase B. Entropía = -0.6 log₂0.6 - 0.4 log₂0.4 ≈ -0.6(-0.737) -0.4(-1.322) = 0.442 + 0.529 = 0.971. Gini = 1 - (0.6²+0.4²) = 1 - (0.36+0.16) = 0.48.

##### 5. Bias-varianza (varianza)

El error de generalización se descompone en:

\[
\text{Error} = \text{Bias}^2 + \text{Varianza} + \text{Ruido}
\]

- **Bias:** Error por suposiciones erróneas del modelo (underfitting).
- **Varianza:** Error por sensibilidad a fluctuaciones en el entrenamiento (overfitting).

**Ejemplo:** Un modelo lineal simple tiene alto bias, baja varianza. Un árbol profundo tiene bajo bias, alta varianza.

##### 6. PCA (matriz de covarianza)

PCA calcula autovalores y autovectores de la matriz de covarianza de los datos centrados. La matriz de covarianza contiene varianzas en la diagonal y covarianzas fuera.

**Ejemplo:** Para dos variables correlacionadas, la matriz de covarianza muestra esa relación. Los autovectores dan las direcciones de máxima varianza.

##### 7. Series de tiempo (autocorrelación)

La autocorrelación mide la correlación de una serie con sus propios rezagos. Útil para identificar patrones estacionales y para modelos ARIMA.

**Ejemplo:** Ventas mensuales con estacionalidad anual mostrarán alta autocorrelación en lag 12.

##### 8. RANSAC (muestreo aleatorio)

RANSAC estima parámetros de un modelo iterativamente, usando muestras aleatorias y evaluando cuántos puntos (inliers) se ajustan al modelo. La probabilidad de éxito depende de la proporción de inliers y del número de iteraciones.

##### 9. Adjusted Rand Index (comparación de clusters)

Mide la similitud entre dos particiones (clustering) ajustando por azar. Se basa en conteos de pares de puntos en el mismo o diferente cluster.

##### 10. Shapley (valor esperado)

Los valores de Shapley, de teoría de juegos cooperativos, distribuyen el "pago" (predicción) entre características según su contribución marginal promedio. Se basan en esperanzas sobre todas las posibles coaliciones.

**Ejemplo:** Para un modelo de crédito, el valor Shapley de "ingresos" puede ser +0.3 (aumenta la probabilidad de aprobación en 0.3), mientras que "deuda" puede ser -0.2.

##### 11. Tests A/B (significancia)

En experimentos A/B, se comparan dos versiones (A y B) y se usa un test estadístico (t-test, chi-cuadrado) para determinar si las diferencias observadas son significativas (p-valor < 0.05) o debidas al azar.

**Ejemplo:** Tasa de conversión: A 5.2%, B 5.8% con n=1000. Un test de proporciones puede dar p=0.03, indicando mejora significativa.

#### Deep Learning (DL)

##### 1. Dropout (Bernoulli)

Dropout es una técnica de regularización que durante entrenamiento "apaga" aleatoriamente neuronas con probabilidad p. Se implementa multiplicando la salida de una capa por una máscara de variables Bernoulli independientes (0 o 1). La probabilidad de mantener una neurona suele ser 0.5.

**Ejemplo:** En una capa con 1000 neuronas, dropout con p=0.5 genera una máscara con ~500 unos y 500 ceros, multiplicando la activación.

##### 2. Inicialización de pesos (varianza)

La inicialización adecuada controla la varianza de las activaciones para evitar gradientes evanescentes/explosivos.

- **Xavier (Glorot):** Var(W) = 2/(n_in + n_out)
- **He:** Var(W) = 2/n_in (para ReLU)

**Ejemplo:** Una capa con 256 entradas y 512 salidas, inicialización He: desviación estándar = √(2/256) ≈ 0.088. Los pesos se muestrean de una normal N(0, 0.088²).

##### 3. Batch Normalization (media, varianza)

Batch Norm normaliza las activaciones de una capa usando la media y varianza del mini-batch:

\[
\hat{x} = \frac{x - \mu_B}{\sqrt{\sigma_B^2 + \epsilon}}, \quad y = \gamma \hat{x} + \beta
\]

Luego aprende parámetros de escala γ y desplazamiento β. Durante entrenamiento, mantiene medias móviles de μ y σ para usar en inferencia.

**Ejemplo:** En una CNN con batch size 32, para un canal con 64 valores por imagen, se calculan media y varianza sobre esos 32×64 = 2048 valores.

##### 4. Modelos de lenguaje (probabilidad de secuencias)

Los modelos de lenguaje autoregresivos (como GPT) modelan la probabilidad de una secuencia como producto de probabilidades condicionales:

\[
P(x_1, x_2, \dots, x_T) = \prod_{t=1}^T P(x_t | x_{<t})
\]

Cada \(P(x_t | x_{<t})\) es una distribución sobre el vocabulario (softmax). El entrenamiento maximiza la log-verosimilitud.

**Ejemplo:** Para la frase "el gato come", la probabilidad se descompone como P(el) × P(gato|el) × P(come|el,gato).

##### 5. Modelos generativos (distribuciones, divergencia KL)

- **VAE (Variational Autoencoder):** Minimiza la divergencia KL entre la distribución posterior aproximada \(q(z|x)\) y la prior \(p(z)\) (normal estándar). La pérdida es:
  \[
  L = \text{Reconstrucción} + D_{KL}(q(z|x) \parallel p(z))
  \]
- **GANs:** La distribución generada \(p_g\) se compara implícitamente con la real \(p_{data}\) mediante el discriminador.

**Ejemplo:** En VAE, la divergencia KL tiene fórmula cerrada para Gaussianas:  
\(D_{KL}(N(\mu, \sigma^2) \parallel N(0,1)) = -\frac{1}{2}(1 + \log \sigma^2 - \mu^2 - \sigma^2)\)

##### 6. CLIP (softmax, pérdida contrastiva)

CLIP entrena un modelo para alinear imágenes y textos en un espacio común. Usa una pérdida contrastiva basada en softmax sobre similitudes coseno:

\[
L = -\log \frac{\exp(\text{sim}(I_i, T_i)/\tau)}{\sum_{j=1}^N \exp(\text{sim}(I_i, T_j)/\tau)} - \log \frac{\exp(\text{sim}(I_i, T_i)/\tau)}{\sum_{j=1}^N \exp(\text{sim}(I_j, T_i)/\tau)}
\]

Esto maximiza la similitud entre pares correctos y minimiza con pares incorrectos.

**Ejemplo:** Para un batch de 32 pares imagen-texto, se calcula la matriz de similitud 32×32. La pérdida contrastiva hace que los elementos diagonales tengan alta probabilidad bajo softmax por filas y por columnas.

---

