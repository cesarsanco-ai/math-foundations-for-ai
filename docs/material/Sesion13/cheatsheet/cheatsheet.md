---
layout: default
---

# Cheatsheet: Cálculo multivariable
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-13](../../../sesiones/sesion-13.md)

---

## Gradiente

\[
\nabla f = \left(\frac{\partial f}{\partial x_1},\ldots,\frac{\partial f}{\partial x_n}\right)^\top
\]

Dirección de **máximo** ascenso.

---

## Jacobiano (vector → vector)

\(J_{ij} = \partial y_i / \partial x_j\) — matriz \(m\times n\)

---

## Hessiano (escalar → matriz)

\(H_{ij} = \partial^2 f / \partial x_i \partial x_j\) — simétrica si \(f\in C^2\)

---

## Descenso

\(\theta \leftarrow \theta - \eta \nabla L(\theta)\)

---

## torch (gradiente)

```python
loss = model(x).sum()
loss.backward()          # d(loss)/d(params)
for p in model.parameters():
    p.data -= lr * p.grad
```

---

## Puntos críticos

* **Punto silla:** gradiente cero pero Hessiano indefinido.
* En DL, \(H\) es enorme; se usan **aproximaciones** o solo primer orden.

> *“El gradiente es el vector de sensibilidades de la pérdida respecto a cada parámetro.”*
