---
layout: default
---

# Cheatsheet: Transformaciones lineales
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-06](../../../sesiones/sesion-06.md)

---

## Linealidad

\(T(\alpha\mathbf{u}+\beta\mathbf{v})=\alpha T(\mathbf{u})+\beta T(\mathbf{v})\)

---

## Matriz de \(T\)

Columna \(j\) = imagen de \(\mathbf{e}_j\): \(A=[T(\mathbf{e}_1)\,\cdots\,T(\mathbf{e}_n)]\)

---

## Composición

Matriz de \(S\circ T\) = \(A_S\,A_T\) (orden: primero \(T\), luego \(S\))

---

## Rotación 2D

\[
R_\theta=\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}
\]

---

## PyTorch (capa lineal)

```python
import torch.nn as nn
layer = nn.Linear(in_features, out_features, bias=True)
# y = layer(x)  implementa y = x @ W.T + b
```

---

## Puntos críticos

* Sin activaciones, **\(W_2 W_1\)** es una sola transformación; la profundidad aporta rango efectivo y regularización implícita, pero no nuevas direcciones no lineales.
* **Data augmentation** (rotaciones, escalados) aplica transformaciones lineales (o afines) a entradas.

> *“La composición + no linealidad es lo que hace expresivas las redes profundas.”*
