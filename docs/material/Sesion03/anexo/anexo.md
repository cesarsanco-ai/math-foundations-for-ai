---
layout: default
---

# Fundamento: matrices, operaciones y datos tabulares
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-03](../../../sesiones/sesion-03.md)

*(Alineado con la teoría de la Semana 3: [sesion3.md](../teoria/sesion3.md).)*

---

## 1. Definición y tipos

Matriz \(A\in\mathbb{R}^{m\times n}\); elementos \(a_{ij}\). **Cuadrada, diagonal,** \(I_n\), **triangular** superior/inferior.

---

## 2. Operaciones fundamentales

- **Suma** (mismo tamaño): \((A+B)_{ij}=a_{ij}+b_{ij}\).
- **Producto:** \(C=AB\), \(c_{ij}=\sum_k a_{ik}b_{kj}\); en general \(AB\neq BA\).
- **Matriz–vector:** \((A\mathbf{x})_i=\sum_j a_{ij}x_j\).
- **Transpuesta:** \((A^\top)_{ij}=a_{ji}\).

---

## 3. Determinante, inversa y rango

- \(\det(A)\) en \(2\times2\): \(ad-bc\). **Inversa** \(A^{-1}\) si \(\det\neq 0\).
- **Rango:** dimensión del espacio fila/columna; indica redundancia de features.

---

## 4. Datos como matriz de diseño

\(X\in\mathbb{R}^{n\times d}\): filas = muestras, columnas = features. Con columna de unos,

\[
\hat{\mathbf{y}} = X_{\text{aug}}\boldsymbol{\theta},\qquad
\boldsymbol{\theta}=(X_{\text{aug}}^\top X_{\text{aug}})^{-1}X_{\text{aug}}^\top \mathbf{y}
\]

(mínimos cuadrados cuando el rango es adecuado).

---

## 5. Conexión con ML / DL

- **Regresión logística:** \(\mathbf{z}=X\mathbf{w}+\mathbf{b}\), luego sigmoide/softmax.
- **PCA:** covarianza \(\Sigma\propto X^\top X\) (datos centrados).
- **Capa lineal:** \(\mathbf{h}=W\mathbf{x}+\mathbf{b}\); **backprop:** \(\partial L/\partial W = (\partial L/\partial \mathbf{h})\mathbf{x}^\top\).

---

## 6. Enlaces directos

* **Teoría completa:** [sesion3.md](../teoria/sesion3.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Ecuaciones clave

| Concepto | Expresión |
|----------|-----------|
| Producto | \(c_{ij}=\sum_k a_{ik}b_{kj}\) |
| OLS | \(\boldsymbol{\theta}=(X^\top X)^{-1}X^\top \mathbf{y}\) |
| Covarianza (empírica) | \(\Sigma=\frac{1}{n-1}X^\top X\) (centrada) |
