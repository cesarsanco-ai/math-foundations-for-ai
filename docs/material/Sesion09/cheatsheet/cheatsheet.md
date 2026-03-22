---
layout: default
---

# Cheatsheet: Tensores
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-09](../../../sesiones/sesion-09.md)

---

## Shapes típicos

| Dato | Shape |
| :--- | :--- |
| Batch imágenes RGB | `(N, H, W, 3)` o `(N, 3, H, W)` |
| Secuencia | `(batch, seq_len, dim)` |
| Video | `(N, T, H, W, C)` |

---

## Broadcasting (reglas)

1. Alinear ejes por la **derecha**.
2. Compatible si igual o **1**.
3. `1` se “estira”.

---

## NumPy / PyTorch

```python
import torch
x = torch.randn(4, 3, 224, 224)   # NCHW
y = x.permute(0, 2, 3, 1)         # NHWC si hace falta
z = x.reshape(4, -1)               # flatten espacial
```

---

## Operaciones

| Nombre | Descripción |
| :--- | :--- |
| `einsum` | Contracciones explícitas |
| `@` / `matmul` | Producto matricial / por lotes |
| `*` | Producto elemento a elemento |

---

## Puntos críticos

* **Contiguous** tras `permute` antes de `view` (PyTorch).
* Broadcasting evita bucles pero puede **ocultar** copias grandes en memoria.

> *“El batch dimension es el primer eje en casi todos los pipelines de entrenamiento.”*
