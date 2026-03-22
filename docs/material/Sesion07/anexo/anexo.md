---
layout: default
---

# Fundamento: autovalores, autovectores y diagonalización
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-07](../../../sesiones/sesion-07.md)

*(Alineado con la teoría de la Semana 7: [sesion7.md](../teoria/sesion7.md).)*

---

## 1. Definición

\(A\mathbf{v}=\lambda\mathbf{v}\), \(\mathbf{v}\neq\mathbf{0}\). \(\lambda\) = autovalor; \(\mathbf{v}\) = autovector (dirección invariante salvo escala).

---

## 2. Ecuación característica

\((A-\lambda I)\mathbf{v}=\mathbf{0}\) no trivial \(\Rightarrow\) \(\det(A-\lambda I)=0\). Raíces del polinomio característico = autovalores.

---

## 3. Diagonalización

Si hay \(n\) autovectores independientes: \(A=PDP^{-1}\) con \(D=\operatorname{diag}(\lambda_1,\dots,\lambda_n)\). Entonces \(A^k=PD^kP^{-1}\).

Matrices **simétricas:** \(A=Q\Lambda Q^\top\) con \(Q\) ortogonal (descomposición espectral).

---

## 4. Aplicaciones en IA

- **PCA:** autovectores de la matriz de covarianza = direcciones de máxima varianza.
- **Estabilidad RNN:** radios espectrales / autovalores de pesos recurrentes.
- **Análisis de Hessiana** (segundas derivadas): curvatura en optimización.

---

## 5. Enlaces directos

* **Teoría completa:** [sesion7.md](../teoria/sesion7.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 6. Resumen

| Concepto | Recordatorio |
|----------|--------------|
| \(\det(A-\lambda I)=0\) | Encuentra \(\lambda\) |
| Traza / determinante | Relacionados con \(\lambda_i\) en \(n\times n\) |
| Simétrica | \(\lambda_i\in\mathbb{R}\), bases ortogonales |
