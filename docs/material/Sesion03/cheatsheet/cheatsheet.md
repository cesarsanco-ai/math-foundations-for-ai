---
layout: default
---

# Cheatsheet: Matrices
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-03](../../../sesiones/sesion-03.md)

---

## Tamaños

| Expresión | Requiere |
| :--- | :--- |
| \(A+B\) | Mismas dimensiones |
| \(AB\) | cols\(A\)=filas\(B\) |
| \(A\mathbf{x}\) | \(\mathbf{x}\) largo \(n\), \(A\) es \(m\times n\) |

---

## \(2\times 2\)

\[
\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc,\quad
A^{-1}=\frac{1}{\det}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}
\]

---

## Dataset

| Objeto | Dimensión |
| :--- | :--- |
| \(X\) | \(n_{\text{samples}}\times n_{\text{features}}\) |
| \(\mathbf{y}\) | \(n_{\text{samples}}\times 1\) |

---

## Regresión lineal (OLS)

\[
\boldsymbol{\theta}=(X^\top X)^{-1}X^\top \mathbf{y}
\]

---

## NumPy

```python
import numpy as np
X = np.array([[1, x1], [1, x2]])   # diseño con bias
y = np.array([y1, y2])
theta = np.linalg.lstsq(X, y, rcond=None)[0]
# o: theta = np.linalg.solve(X.T @ X, X.T @ y)
```

---

## Puntos críticos

* **No conmutatividad:** \(AB\neq BA\) en general.
* **Condicionamiento:** \(X^\top X\) mal condicionada → regularizar (Ridge) o SVD.

> *“Cada fila de \(X\) es un ejemplo; cada columna, una feature.”*
