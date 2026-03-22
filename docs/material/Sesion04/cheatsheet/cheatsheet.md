---
layout: default
---

# Cheatsheet: Sistemas de ecuaciones lineales
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-04](../../../sesiones/sesion-04.md)

---

## Forma \(A\mathbf{x}=\mathbf{b}\)

| Caso | Condición | Solución |
| :--- | :--- | :--- |
| Cuadrado | \(\det(A)\neq 0\) | Única |
| Rango \(<n\) | Dependencia | \(\infty\) o vacío |
| \(m>n\) | Sin solución exacta | Mínimos cuadrados |

---

## Mínimos cuadrados

\[
\min_{\mathbf{x}}\|A\mathbf{x}-\mathbf{b}\|_2^2
\;\Rightarrow\;
A^\top A\mathbf{x}=A^\top \mathbf{b}
\]

---

## Regresión ↔ MC

\(X\boldsymbol{\theta}\approx\mathbf{y}\) ⇒ \(\boldsymbol{\theta}=(X^\top X)^{-1}X^\top\mathbf{y}\)

---

## NumPy / SciPy

```python
import numpy as np
x = np.linalg.lstsq(A, b, rcond=None)[0]
# o np.linalg.solve(A.T @ A, A.T @ b) si A.T@A es invertible
```

---

## Puntos críticos

* **Estabilidad:** usar `lstsq` o SVD frente a formar \(A^\top A\) en mal condicionamiento.
* Geometría: residual \(\mathbf{b}-A\mathbf{x}^*\) ortogonal a columnas de \(A\).

> *“OLS es proyección ortogonal de \(\mathbf{y}\) sobre el espacio columna de \(X\).”*
