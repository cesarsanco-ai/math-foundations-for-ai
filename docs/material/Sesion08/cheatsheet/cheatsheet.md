---
layout: default
---

# Cheatsheet: Descomposición de matrices (SVD)
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-08](../../../sesiones/sesion-08.md)

---

## SVD

\[
A = U \Sigma V^\top,\quad \sigma_1 \ge \cdots \ge \sigma_r > 0
\]

---

## Truncada (rango \(k\))

\(A \approx U_k \Sigma_k V_k^\top\) — error en norma Frobenius controlado por \(\sigma_{k+1},\dots\)

---

## Pseudoinversa

\(A^+ = V \Sigma^+ U^\top\); \(\Sigma^+_{ii}=1/\sigma_i\) si \(\sigma_i>0\)

---

## NumPy

```python
import numpy as np
U, s, Vt = np.linalg.svd(A, full_matrices=False)
# reconstrucción: U @ np.diag(s) @ Vt
A_pinv = np.linalg.pinv(A)
```

---

## Uso típico

| Tarea | Rol de SVD |
| :--- | :--- |
| MC mal condicionado | Estabilizar vs \((A^\top A)^{-1}\) |
| Reducción dim. | Truncar \(\Sigma\) |
| LoRA / bajo rango | Actualizar suma de productos externos |

---

## Puntos críticos

* **Valores singulares pequeños** amplifican ruido al invertir → regularización o truncar.
* En **PCA** (centrado), SVD de \(X\) relacionado con autovectores de covarianza.

> *“SVD descompone cualquier matriz rectangular en rotaciones y escalados.”*
