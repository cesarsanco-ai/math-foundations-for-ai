---
layout: default
---

# Cheatsheet: Espacios vectoriales y normas
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-05](../../../sesiones/sesion-05.md)

---

## Normas

| Nombre | \(\|\mathbf{x}\|\) | Comentario |
| :--- | :--- | :--- |
| **L2** | \(\sqrt{\sum x_i^2}\) | Diferenciable en \(x\neq 0\) |
| **L1** | \(\sum \|x_i\|\) | Promueve sparsity |
| **L∞** | \(\max_i \|x_i\|\) | Caja / robustez uniforme |

---

## Distancias

| Métrica | Fórmula |
| :--- | :--- |
| Euclídea | \(\|\mathbf{a}-\mathbf{b}\|_2\) |
| Manhattan | \(\|\mathbf{a}-\mathbf{b}\|_1\) |
| Chebyshev | \(\|\mathbf{a}-\mathbf{b}\|_\infty\) |

---

## Similitud coseno

\[
\text{cos\_sim}(\mathbf{u},\mathbf{v})=\frac{\mathbf{u}\cdot\mathbf{v}}{\|\mathbf{u}\|_2\|\mathbf{v}\|_2}
\]

---

## sklearn (referencia)

```python
from sklearn.metrics.pairwise import cosine_similarity, euclidean_distances
# cosine_similarity(X, Y); euclidean_distances(X, Y)
```

---

## Puntos críticos

* **Estandarizar** features antes de comparar normas o distancias.
* Ridge **penaliza** magnitud global de pesos; Lasso **anula** coordenadas.

> *“La norma que elijas define la geometría del error.”*
