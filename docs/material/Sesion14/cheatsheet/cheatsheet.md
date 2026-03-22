---
layout: default
---

# Cheatsheet: Optimización y gradiente descendente
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-14](../../../sesiones/sesion-14.md)

---

## GD clásico

\[
\theta_{t+1} = \theta_t - \eta \nabla L(\theta_t)
\]

---

## SGD / mini-batch

Usar \(\nabla L_{\mathcal{B}}\) en un subconjunto \(\mathcal{B}\) — más rápido, más ruido.

---

## Momentum (idea)

\(v_t = \beta v_{t-1} + \nabla L\); \(\theta \leftarrow \theta - \eta v_t\)

---

## Adam (idea)

Estimación adaptativa de momentos de orden 1 y 2 de los gradientes; \(\beta_1,\beta_2,\epsilon\) por defecto en frameworks.

---

## PyTorch

```python
opt = torch.optim.Adam(model.parameters(), lr=1e-3, weight_decay=1e-4)
opt.zero_grad()
loss.backward()
opt.step()
```

---

## Heurísticas

| Tema | Consejo |
| :--- | :--- |
| `lr` | schedulers (cosine, step decay) |
| Batch size | trade-off memoria vs ruido |
| Early stopping | parar al subir val loss |

---

## Puntos críticos

* **Convexidad** (OLS, logistic convex en muchos casos) ≠ **deep nets**.
* **Weight decay** \(\neq\) siempre lo mismo que L2 en Adam (implementación depende del optimizador).

> *“El gradiente es barato; la curvatura exacta (Hessiano) suele ser prohibitiva.”*
