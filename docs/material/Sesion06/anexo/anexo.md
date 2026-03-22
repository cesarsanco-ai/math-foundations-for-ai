---
layout: default
---

# Fundamento: transformaciones lineales y composición de capas
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-06](../../../sesiones/sesion-06.md)

*(Alineado con la teoría de la Semana 6: [sesion6.md](../teoria/sesion6.md).)*

---

## 1. Definición

\(T:\mathbb{R}^n\to\mathbb{R}^m\) es **lineal** si \(T(\mathbf{u}+\mathbf{v})=T(\mathbf{u})+T(\mathbf{v})\) y \(T(\alpha\mathbf{u})=\alpha T(\mathbf{u})\).

---

## 2. Matriz asociada

Siempre existe \(A\in\mathbb{R}^{m\times n}\) tal que \(T(\mathbf{x})=A\mathbf{x}\); columnas de \(A\) son \(T(\mathbf{e}_1),\dots,T(\mathbf{e}_n)\).

---

## 3. Composición

\((S\circ T)(\mathbf{x})=S(T(\mathbf{x}))\) con matriz **\(B A\)** si \(T\sim A\), \(S\sim B\) (dimensiones compatibles).

---

## 4. Ejemplos geométricos

- **Rotación 2D:** \(R_\theta=\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}\).
- **Escalado:** \(\operatorname{diag}(s_x,s_y)\).
- **Proyección** sobre recta con dirección unitaria \(\mathbf{u}\): \(P=\mathbf{u}\mathbf{u}^\top\).

---

## 5. Red neuronal sin activación

Composición de capas lineales \(W_L\cdots W_1\) equivale a **una sola** transformación lineal si no hay no linealidad (rango acotado).

---

## 6. Enlaces directos

* **Teoría completa:** [sesion6.md](../teoria/sesion6.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Resumen

| Idea | Formalismo |
|------|------------|
| Capa lineal | \(\mathbf{h}=W\mathbf{x}+\mathbf{b}\) |
| Varias capas lineales | Producto de matrices |
| No linealidad | ReLU, sigmoide, etc. entre capas |
