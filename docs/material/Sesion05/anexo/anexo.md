---
layout: default
---

# Fundamento: espacios vectoriales, normas y geometría para ML
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-05](../../../sesiones/sesion-05.md)

*(Alineado con la teoría de la Semana 5: [sesion5.md](../teoria/sesion5.md).)*

---

## 1. Espacio \(\mathbb{R}^n\) y subespacios

Combinaciones lineales, independencia, base y dimensión. Cambio de base = nueva representación de los mismos vectores.

---

## 2. Producto interno y ángulo

\[
\mathbf{u}\cdot\mathbf{v}=\sum_i u_i v_i=\|\mathbf{u}\|\|\mathbf{v}\|\cos\theta
\]

**Similitud coseno:** \(\frac{\mathbf{u}\cdot\mathbf{v}}{\|\mathbf{u}\|\|\mathbf{v}\|}\) (documentos, embeddings).

---

## 3. Normas y distancias

| Norma | Definición | Uso típico |
|-------|------------|------------|
| \(L_2\) | \(\sqrt{\sum_i x_i^2}\) | Euclídea, Ridge |
| \(L_1\) | \(\sum_i \|x_i\|\) | Lasso, robustez |
| \(L_\infty\) | \(\max_i \|x_i\|\) | Chebyshev |

Distancias inducidas: \(\|\mathbf{x}-\mathbf{y}\|_p\).

---

## 4. Proyecciones e hiperplanos

Proyección ortogonal sobre subespacio; **hiperplano** \(\mathbf{w}^\top\mathbf{x}+b=0\) separa semiespacios (SVM).

---

## 5. Regularización

\[
L(\theta)=\text{Loss}+\lambda\|\theta\|_2^2\quad\text{(Ridge)};\quad
L(\theta)=\text{Loss}+\lambda\|\theta\|_1\quad\text{(Lasso)}
\]

---

## 6. Enlaces directos

* **Teoría completa:** [sesion5.md](../teoria/sesion5.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Aplicaciones rápidas

| Tema | Objeto matemático |
|------|-------------------|
| KNN | \(\|\mathbf{x}-\mathbf{x}_i\|_2\) |
| SVM | Margen, producto con normal |
| Attention | \(QK^\top\) (similitudes) |
| LoRA | Normas de matrices de bajo rango |
