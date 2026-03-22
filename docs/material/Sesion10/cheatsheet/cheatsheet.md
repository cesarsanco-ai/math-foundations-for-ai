---
layout: default
---

# Cheatsheet: Probabilidad y estadística para IA
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-10](../../../sesiones/sesion-10.md)

---

## Bayes

\[
P(A|B)=\frac{P(B|A)P(A)}{P(B)}
\]

---

## Esperanza y varianza

\(E[X]=\sum x_i p_i\) (discreta); \(\operatorname{Var}(X)=E[X^2]-E[X]^2\)

---

## Correlación

\[
\rho_{XY}=\frac{\operatorname{Cov}(X,Y)}{\sigma_X\sigma_Y}\in[-1,1]
\]

---

## Entropía

\(H(p)=-\sum_i p_i\log p_i\) — base 2 (bits) o \(e\) (nats)

---

## Python

```python
import numpy as np
from scipy import stats
stats.norm.pdf(x, loc=0, scale=1)
np.corrcoef(a, b)
```

---

## Puntos críticos

* **Independencia** \(\neq\) incorrelación (salvo gaussianas conjuntas en condiciones).
* Métricas de clasificación (precision/recall) dependen de **prevalencia** y umbral.

> *“La regla de Bayes conecta creencias previas con evidencia observada.”*
