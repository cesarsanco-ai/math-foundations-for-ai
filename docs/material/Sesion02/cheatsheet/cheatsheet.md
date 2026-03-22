---
layout: default
---

# Cheatsheet: Fundamentos de IA
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-02](../../../sesiones/sesion-02.md)

---

## Tipos de aprendizaje

| Tipo | Datos | Objetivo |
| :--- | :--- | :--- |
| **Supervisado** | Etiquetas | Regresión / clasificación |
| **No supervisado** | Sin etiquetas | Clustering, densidad, reducción |
| **Refuerzo** | Recompensas | Política, secuencias |

---

## Pipeline conceptual

1. \(f(x;\theta)\) — modelo  
2. \(\ell(y,\hat y)\) — pérdida puntual  
3. \(L(\theta)=\frac{1}{n}\sum_i \ell_i\) — costo  
4. \(\min_\theta L\) — entrenamiento  

---

## Pérdidas rápidas

| Problema | Fórmula |
| :--- | :--- |
| MSE | \(\frac{1}{n}\sum (y_i-\hat y_i)^2\) |
| MAE | \(\frac{1}{n}\sum \|y_i-\hat y_i\|\) |
| Log-loss binaria | \(-\frac{1}{n}\sum [y_i\log\hat y_i+(1-y_i)\log(1-\hat y_i)]\) |
| Hinge (SVM) | \(\max(0,1-y\,\hat y)\) |

---

## Optimización

| Método | Actualización (idea) |
| :--- | :--- |
| GD | \(\theta\leftarrow\theta-\eta\nabla L\) |
| SGD | Mismo con gradiente en un mini-batch |
| Adam | Tasas adaptativas (momentos) |

---

## Regularización

\[
L = \text{data loss} + \lambda \|\theta\|_2^2 \quad \text{(Ridge)};\quad
L = \text{data loss} + \lambda \|\theta\|_1 \quad \text{(Lasso)}
\]

---

## Python (boceto)

```python
import torch
import torch.nn as nn
loss_fn = nn.MSELoss()          # o CrossEntropyLoss, etc.
optimizer = torch.optim.Adam(model.parameters(), lr=1e-3)
```

---

## Puntos críticos

* Alinear **métrica de entrenamiento** con el **negocio** (accuracy puede engañar).
* **Loss** vs **cost**: a veces loss por ejemplo; cost = promedio/suma en el set.

> *“Solo cambian modelo, pérdida y optimizador; el resto es ingeniería y datos.”*
