---
layout: default
---
# Sesión 1: Fundamentos Matemáticos - Solucionario NTB1

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye procedimiento detallado y cierre conceptual aplicado.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Notación y sumatoria ponderada

**Enunciado (contexto IA):** En un mini-batch de 4 muestras, los errores absolutos son $e=(0.2,0.5,0.1,0.4)$ y los pesos de importancia son $w=(1,2,1,3)$. Calcula la pérdida ponderada $L=\frac{\sum_i w_ie_i}{\sum_i w_i}$.

**Solución paso a paso:**

1) Calcula numerador: $1\cdot0.2+2\cdot0.5+1\cdot0.1+3\cdot0.4=2.5$.
2) Calcula denominador: $1+2+1+3=7$.
3) Divide: $L=2.5/7=0.3571$.
4) Interpretación IA: muestras con mayor peso (difíciles o minoritarias) impactan más en el entrenamiento.

### Ejercicio 2: Composición de funciones en una red

**Enunciado (contexto IA):** Sea $f(x)=2x-1$ (capa lineal) y $g(x)=\max(0,x)$ (ReLU). Evalúa $(g\circ f)(x)$ para $x\in\{-1,0,2\}$.

**Solución paso a paso:**

1) Para $x=-1$: $f(-1)=-3$, luego $g(-3)=0$.
2) Para $x=0$: $f(0)=-1$, luego $g(-1)=0$.
3) Para $x=2$: $f(2)=3$, luego $g(3)=3$.
4) Salidas: $(0,0,3)$.
5) En IA, esta composición modela una neurona con activación no lineal.

### Ejercicio 3: Sigmoide y decisión binaria

**Enunciado (contexto IA):** Con logit $z=1.4$, calcula $\sigma(z)=\frac{1}{1+e^{-z}}$ y decide clase con umbral 0.5.

**Solución paso a paso:**

1) $e^{-1.4}\approx0.2466$.
2) $\sigma(1.4)=1/(1+0.2466)=0.8022$.
3) Como $0.8022>0.5$, clase positiva.
4) En clasificación de spam, esto equivale a probabilidad alta de spam.

### Ejercicio 4: Cross-entropy de un ejemplo

**Enunciado (contexto IA):** Para etiqueta real $y=1$ y probabilidad predicha $\hat y=0.73$, calcula $L=-\log(\hat y)$.

**Solución paso a paso:**

1) Sustituye: $L=-\log(0.73)$.
2) Resultado numérico: $L\approx0.3147$.
3) Si $\hat y$ sube hacia 1, la pérdida baja.
4) Esto guía al optimizador a mejorar predicciones correctas.

### Ejercicio 5: ReLU por tramos

**Enunciado (contexto IA):** Evalúa ReLU en $x=(-2,-0.1,0,1.5)$ y explica saturación.

**Solución paso a paso:**

1) ReLU$(x)=\max(0,x)$.
2) Salidas: $(0,0,0,1.5)$.
3) En negativos el gradiente es 0 (neurona apagada).
4) En positivos gradiente 1, favorece aprendizaje estable en redes profundas.

### Ejercicio 6: Softmax de 2 clases

**Enunciado (contexto IA):** Con logits $(2.0,0.5)$ calcula probabilidades softmax.

**Solución paso a paso:**

1) Exponenciales: $(e^2,e^{0.5})\approx(7.389,1.649)$.
2) Suma: $9.038$.
3) Probabilidades: $(0.817,0.183)$.
4) IA: interpreta confianza del modelo en clasificación multiclase.

### Ejercicio 7: MSE de mini-batch

**Enunciado (contexto IA):** $y=(3,0,-1)$ y $\hat y=(2.5,0.2,-0.4)$. Calcula MSE.

**Solución paso a paso:**

1) Errores: $(0.5,-0.2,-0.6)$.
2) Cuadrados: $(0.25,0.04,0.36)$.
3) Promedio: $(0.25+0.04+0.36)/3=0.2167$.
4) Penaliza más errores grandes, útil en regresión.

### Ejercicio 8: Positional encoding simplificado

**Enunciado (contexto IA):** Calcula $\sin(\pi/6)$ y $\cos(\pi/3)$ para ilustrar codificación posicional.

**Solución paso a paso:**

1) $\sin(\pi/6)=0.5$.
2) $\cos(\pi/3)=0.5$.
3) Estas funciones periódicas codifican posición relativa en Transformers.
4) Permiten a atención distinguir orden sin recurrencia.

### Ejercicio 9: Regularización L2

**Enunciado (contexto IA):** Si loss base es 0.82, $\lambda=0.01$, y $||w||_2^2=35$, calcula objective.

**Solución paso a paso:**

1) Término de regularización: $0.01\cdot35=0.35$.
2) Objective total: $0.82+0.35=1.17$.
3) L2 desincentiva pesos grandes.
4) Reduce sobreajuste en modelos de alta capacidad.

### Ejercicio 10: Producto punto como score

**Enunciado (contexto IA):** Dados embeddings $q=(1,2,1)$ y $k=(0,1,3)$, calcula $q\cdot k$.

**Solución paso a paso:**

1) Multiplica componente a componente: $(0,2,3)$.
2) Suma: $5$.
3) Score alto sugiere mayor similitud/alineación.
4) En atención, estos scores se normalizan con softmax.
