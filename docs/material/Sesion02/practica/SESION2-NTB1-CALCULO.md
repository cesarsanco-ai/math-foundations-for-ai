---
layout: default
---
# Sesión 2: Fundamentos de IA - Solucionario NTB1

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye procedimiento detallado y cierre conceptual aplicado.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Pipeline de entrenamiento

**Enunciado (contexto IA):** Para $\hat y=f(x;\theta)=\theta_1x+\theta_0$, con $x=2$, $y=5$, $\theta=(1.2,0.5)$, calcula predicción y error.

**Solución paso a paso:**

1) Predicción: $\hat y=1.2(2)+0.5=2.9$.
2) Error: $e=y-\hat y=2.1$.
3) Error cuadrático: $e^2=4.41$.
4) IA: esta señal alimenta la actualización de parámetros.

### Ejercicio 2: Loss vs cost

**Enunciado (contexto IA):** Con pérdidas individuales $(0.2,0.4,0.8,0.6)$ calcula cost promedio.

**Solución paso a paso:**

1) Suma: $2.0$.
2) Divide por 4: $0.5$.
3) Loss es por muestra, cost es agregada.
4) El optimizador minimiza cost/objective.

### Ejercicio 3: Paso de gradiente

**Enunciado (contexto IA):** Si $\theta=3.0$, $
abla L=1.6$, $\eta=0.05$, actualiza.

**Solución paso a paso:**

1) Regla: $\theta_{new}=\theta-\eta
abla L$.
2) Sustituye: $3-0.05(1.6)=2.92$.
3) La variable se mueve contra gradiente.
4) IA: repitiendo pasos converge a menor pérdida.

### Ejercicio 4: Cross-entropy multiclase

**Enunciado (contexto IA):** Clase real 2 en one-hot $(0,1,0)$ y predicción $(0.1,0.7,0.2)$. Calcula CE.

**Solución paso a paso:**

1) CE$=-\sum y_k\log p_k$.
2) Solo contribuye clase real: $-\log(0.7)$.
3) Resultado: $0.3567$.
4) Penaliza fuerte probabilidades bajas en la clase correcta.

### Ejercicio 5: Regularización en objective

**Enunciado (contexto IA):** Con cost=0.9, $\lambda=0.2$, $R(\theta)=1.5$, calcula objective.

**Solución paso a paso:**

1) Término regularizador: $0.2\cdot1.5=0.3$.
2) Objective: $0.9+0.3=1.2$.
3) Ajusta trade-off sesgo-varianza.
4) Útil para generalizar en datos ruidosos.

### Ejercicio 6: Clasificación de problema

**Enunciado (contexto IA):** Salida: probabilidad de churn, valor continuo de demanda, grupos de clientes. Clasifica tareas.

**Solución paso a paso:**

1) Churn: clasificación binaria.
2) Demanda: regresión.
3) Grupos: clustering no supervisado.
4) Escoger task define loss y métricas.

### Ejercicio 7: ERM con 3 muestras

**Enunciado (contexto IA):** Si $\ell=(0.3,0.1,0.8)$, calcula riesgo empírico.

**Solución paso a paso:**

1) ERM: $\frac{1}{n}\sum\ell_i$.
2) $ (0.3+0.1+0.8)/3=0.4$.
3) Objetivo: minimizar 0.4 hacia abajo.
4) Base formal de casi todo ML supervisado.

### Ejercicio 8: Comparar optimizadores

**Enunciado (contexto IA):** Con gradiente ruidoso en streaming, ¿GD o SGD? justifica con cálculo simple de costo computacional por paso.

**Solución paso a paso:**

1) GD usa todo dataset por paso: costo $O(n)$.
2) SGD usa 1 muestra/mini-batch: costo $O(1)$ o $O(b)$.
3) Para streaming, SGD es viable y rápido.
4) IA en producción usa mini-batch por escalabilidad.

### Ejercicio 9: Matriz de confusión simple

**Enunciado (contexto IA):** TP=40, FP=10, FN=5. Calcula precisión y recall.

**Solución paso a paso:**

1) Precisión: $TP/(TP+FP)=40/50=0.8$.
2) Recall: $TP/(TP+FN)=40/45=0.8889$.
3) Alta recuperación con precisión moderada.
4) En fraude/spam, recall suele ser crítico.

### Ejercicio 10: Learning rate scheduling

**Enunciado (contexto IA):** Si $\eta_0=0.1$ y step decay reduce 50% en época 10, ¿\eta en época 20?

**Solución paso a paso:**

1) Época 10: $0.1\to0.05$.
2) Época 20: $0.05\to0.025$.
3) LR menor estabiliza convergencia final.
4) Práctica estándar en entrenamiento profundo.
