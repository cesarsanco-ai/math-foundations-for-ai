---
layout: default
---

# Fundamento: derivadas, regla de la cadena e integrales (AUC)
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-12](../../../sesiones/sesion-12.md)

*(Alineado con la teoría de la Semana 12: [sesion12.md](../teoria/sesion12.md).)*

---

## 1. Derivada

\[
f'(x_0)=\lim_{h\to 0}\frac{f(x_0+h)-f(x_0)}{h}
\]

Interpretación: pendiente tangente, tasa de cambio.

---

## 2. Reglas

**Producto,** **cociente,** **cadena:** \((f\circ g)'=f'(g(x))g'(x)\).

---

## 3. Derivadas útiles en DL

| Función | Derivada |
|---------|----------|
| \(\sigma(x)\) | \(\sigma(1-\sigma)\) |
| \(\tanh x\) | \(1-\tanh^2 x\) |
| ReLU | \(1_{x>0}\) (a.e.) |

---

## 4. Integral y TFC

\(\int_a^b f(x)\,dx = F(b)-F(a)\) si \(F'=f\).

**AUC-ROC:** área bajo curva sensibilidad vs 1-especificidad (integral / trapezoidal).

---

## 5. Enlaces directos

* **Teoría completa:** [sesion12.md](../teoria/sesion12.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 6. Puente a backprop

Composición de capas \(\Rightarrow\) regla de la cadena en cadena larga = **backpropagation**.
