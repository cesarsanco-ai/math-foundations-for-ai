---
layout: default
---

# Fundamento: gradiente, Jacobiano, Hessiano y superficies de pérdida
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-13](../../../sesiones/sesion-13.md)

*(Alineado con la teoría de la Semana 13: [sesion13.md](../teoria/sesion13.md).)*

---

## 1. Funciones \(f:\mathbb{R}^n\to\mathbb{R}\)

**Derivadas parciales** \(\partial f/\partial x_i\); **gradiente**

\[
\nabla f(\mathbf{x})=\left(\frac{\partial f}{\partial x_1},\dots,\frac{\partial f}{\partial x_n}\right)^\top
\]

Apunta hacia **máximo** crecimiento local; **\(-\nabla f\)** hacia descenso.

---

## 2. Regla de la cadena multivariable

Si \(f(\mathbf{x}(\mathbf{u}))\), entonces \(\partial f/\partial u_j=\sum_i (\partial f/\partial x_i)(\partial x_i/\partial u_j)\).

---

## 3. Jacobiano y Hessiano

- **Jacobiano** \(J_{ij}=\partial f_i/\partial x_j\) para \(\mathbf{f}:\mathbb{R}^n\to\mathbb{R}^m\) (backprop acumula productos).
- **Hessiano** \(H_{ij}=\partial^2 f/\partial x_i\partial x_j\): curvatura; autovalores positivos \(\Rightarrow\) mínimo local estricto (condiciones de segundo orden).

---

## 4. Optimización

**Descenso por gradiente** en \(\mathbb{R}^n\): \(\mathbf{x}\leftarrow \mathbf{x}-\eta\nabla f(\mathbf{x})\). **Newton:** usa \(H^{-1}\) (costoso en alta dimensión).

---

## 5. Enlaces directos

* **Teoría completa:** [sesion13.md](../teoria/sesion13.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 6. En ML

\(L(\theta)\) superficie en millones de dimensiones; **SGD** estima \(\nabla L\) con mini-batches; **Adam** adapta tasas por coordenada.
