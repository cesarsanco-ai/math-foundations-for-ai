---
layout: default
---

# Cheatsheet: Derivadas e integrales (1 variable)
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-12](../../../sesiones/sesion-12.md)

---

## Reglas

| Regla | Fórmula |
| :--- | :--- |
| Potencia | \(\frac{d}{dx}x^n = n x^{n-1}\) |
| Producto | \((uv)' = u'v + uv'\) |
| Cadena | \((f(g(x)))' = f'(g(x)) g'(x)\) |

---

## Activaciones

| \(f\) | \(f'\) |
| :--- | :--- |
| \(\sigma(x)\) | \(\sigma(1-\sigma)\) |
| \(\tanh\) | \(1-\tanh^2\) |
| ReLU | 0 o 1 |

---

## Integral definida

\(\int_a^b f = F(b)-F(a)\), \(F'=f\)

---

## AUC (idea)

Área bajo curva ROC ≈ integral numérica de TPR vs FPR.

---

## PyTorch (autograd)

```python
import torch
x = torch.tensor(2.0, requires_grad=True)
y = x**3
y.backward()
print(x.grad)  # 3*x^2 = 12
```

---

## Puntos críticos

* **Sigmoide:** gradiente pequeño en saturación (vanishing).
* **ReLU:** muerte de neuronas si siempre \(x<0\).

> *“Backprop es la regla de la cadena aplicada al grafo de cómputo.”*
