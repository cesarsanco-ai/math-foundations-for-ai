---
layout: default
---

# Fundamento: sistemas lineales, eliminación gaussiana y mínimos cuadrados
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-04](../../../sesiones/sesion-04.md)

*(Alineado con la teoría de la Semana 4: [sesion4.md](../teoria/sesion4.md).)*

---

## 1. Forma matricial

Sistema \(A\mathbf{x}=\mathbf{b}\) con \(A\in\mathbb{R}^{m\times n}\). Cada ecuación es un hiperplano en \(\mathbb{R}^n\).

---

## 2. Clasificación de soluciones

- **Única:** \(A\) cuadrada invertible (rango completo).
- **Infinitas:** variables libres (dependencia lineal entre filas).
- **Inconsistente:** p. ej. pivote en \([A|\mathbf{b}]\) da fila \([0\cdots0|c]\), \(c\neq 0\).

---

## 3. Eliminación gaussiana

Operaciones elementales sobre \([A|\mathbf{b}]\) hasta forma escalonada; sustitución hacia atrás.

---

## 4. Sistemas sobredeterminados y ecuaciones normales

Si \(m>n\) y no hay solución exacta, **mínimos cuadrados** minimiza \(\|A\mathbf{x}-\mathbf{b}\|_2^2\):

\[
A^\top A\mathbf{x}=A^\top \mathbf{b},\qquad
\mathbf{x}=(A^\top A)^{-1}A^\top \mathbf{b}
\]

(interpretación geométrica: proyección de \(\mathbf{b}\) sobre \(\mathcal{C}(A)\)).

---

## 5. Aplicación: regresión lineal

Modelo \(\mathbf{y}\approx X\boldsymbol{\theta}\); misma estructura que mínimos cuadrados. **Ridge** modifica a \((X^\top X+\lambda I)\boldsymbol{\theta}=X^\top\mathbf{y}\).

---

## 6. Enlaces directos

* **Teoría completa:** [sesion4.md](../teoria/sesion4.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Resumen

| Situación | Enfoque |
|-----------|---------|
| \(n\times n\) invertible | Eliminación / \(\mathbf{x}=A^{-1}\mathbf{b}\) |
| Sobredeterminado | Ecuaciones normales o SVD (`lstsq`) |
| Rank deficient | Pseudoinversa, regularización |
