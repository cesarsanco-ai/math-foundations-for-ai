---
layout: default
---

# Cheatsheet: Autovalores y autovectores
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-07](../../../sesiones/sesion-07.md)

---

## Ecuación

\(A\mathbf{v}=\lambda\mathbf{v}\) ⟺ \((A-\lambda I)\mathbf{v}=\mathbf{0}\) ⟺ \(\det(A-\lambda I)=0\)

---

## Diagonalización

\(A=PDP^{-1}\), \(D\) diagonal si hay base de autovectores.

**Simétrica:** \(A=Q\Lambda Q^\top\)

---

## Potencias

\(A^k = P D^k P^{-1}\)

---

## NumPy

```python
import numpy as np
w, v = np.linalg.eig(A)      # autovalores w, columnas de v autovectores
# np.linalg.eigh(A) para simétrica/hermítica (valores reales)
```

---

## PCA (idea)

Covarianza \( \Sigma \); autovectores = componentes principales.

---

## Puntos críticos

* Autovalores **complejos** ⇒ rotación mezclada (no solo escalado en \(\mathbb{R}^n\)).
* **Multiplicidad** y espacios propios afectan diagonalización.

> *“Los autovectores señalan direcciones que la matriz solo escala.”*
