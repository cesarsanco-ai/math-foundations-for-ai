---
layout: default
---

# Fundamento: SVD, bajo rango y pseudoinversa
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-08](../../../sesiones/sesion-08.md)

*(Alineado con la teoría de la Semana 8: [sesion8.md](../teoria/sesion8.md).)*

---

## 1. Descomposición SVD

Para \(A\in\mathbb{R}^{m\times n}\):

\[
A = U\Sigma V^\top
\]

\(U,V\) ortogonales; \(\Sigma\) diagonal con \(\sigma_1\ge\cdots\ge\sigma_r>0\) (valores singulares), \(r=\operatorname{rank}(A)\).

---

## 2. Cálculo conceptual

\(\sigma_i=\sqrt{\lambda_i(A^\top A)}\); columnas de \(V\) = autovectores de \(A^\top A\); columnas de \(U\) relacionadas con \(AA^\top\).

---

## 3. Interpretación geométrica

\(A\mathbf{x}=U\Sigma V^\top\mathbf{x}\): rotación/reflexión → escalado por \(\sigma_i\) → rotación/reflexión. La imagen de la esfera unitaria es un elipsoide.

---

## 4. Pseudoinversa de Moore–Penrose

\[
A^+ = V\Sigma^+ U^\top
\]

\(\Sigma^+\): transponer y sustituir \(\sigma_i>0\) por \(1/\sigma_i\). Solución de mínimos cuadrados de norma mínima: \(\mathbf{x}=A^+\mathbf{b}\).

---

## 5. Aplicaciones

- **Compresión / bajo rango:** \(A\approx U_r\Sigma_r V_r^\top\).
- **Recomendación:** factorización tipo \(R\approx PQ^\top\).
- **LoRA:** actualizaciones de bajo rango sobre pesos.

---

## 6. Enlaces directos

* **Teoría completa:** [sesion8.md](../teoria/sesion8.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Comparación

| Método | Cuándo |
|--------|--------|
| SVD completa | Análisis, truncamiento |
| `lstsq` / `pinv` | Resolver \(A\mathbf{x}\approx\mathbf{b}\) en práctica |
