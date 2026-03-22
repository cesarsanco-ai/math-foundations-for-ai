---
layout: default
---

# Fundamento: convexidad, optimización y variantes del descenso por gradiente
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-14](../../../sesiones/sesion-14.md)

*(Alineado con la teoría de la Semana 14: [sesion14.md](../teoria/sesion14.md).)*

---

## 1. Convexidad

\(f\) convexa si \(f(\lambda x+(1-\lambda)y)\le \lambda f(x)+(1-\lambda)f(y)\). En convexos, **mínimos locales = globales**.

---

## 2. Problema típico

\(\min_\theta L(\theta)\) con \(L\) suave (o subdiferenciable).

---

## 3. Gradiente descendente

\[
\theta \leftarrow \theta - \eta \nabla L(\theta)
\]

\(\eta\) = learning rate; convergencia depende de convexidad y condicionamiento.

---

## 4. Variantes

- **SGD:** gradiente con un ejemplo o mini-batch.
- **Momentum:** acumula velocidad \(v_t=\beta v_{t-1}+\eta\nabla L\).
- **RMSprop / Adam:** tasas adaptativas con medias de gradientes y segundos momentos.

---

## 5. Regularización

Términos \(\lambda\|\theta\|_2^2\), \(\lambda\|\theta\|_1\) en la función objetivo; **weight decay** en SGD.

---

## 6. Enlaces directos

* **Teoría completa:** [sesion14.md](../teoria/sesion14.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. DL vs convexo

Redes profundas: **no convexo**; múltiples mínimos y puntos silla; en la práctica Adam + horario de \(\eta\) + early stopping.
