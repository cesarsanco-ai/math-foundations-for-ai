---
layout: default
---

# Fundamento: límites, continuidad y estabilidad de modelos
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-11](../../../sesiones/sesion-11.md)

*(Alineado con la teoría de la Semana 11: [sesion11.md](../teoria/sesion11.md).)*

---

## 1. Límite

\(\lim_{x\to a}f(x)=L\): definición \(\varepsilon\)-\(\delta\); **límites laterales** deben coincidir para existir el límite bilateral.

---

## 2. Continuidad en \(a\)

1. \(f(a)\) definida; 2. existe \(\lim_{x\to a}f(x)\); 3. límite = \(f(a)\).

**Tipos de discontinuidad:** evitable, salto, infinita, esencial.

---

## 3. Teoremas en intervalos compactos

- **Valor intermedio:** si \(f\) continua en \([a,b]\), toma todos los valores entre \(f(a)\) y \(f(b)\).
- **Weierstrass:** máximo y mínimo absolutos en \([a,b]\).

---

## 4. Conexión con IA

- **Pérdidas** continuas (salvo puntos de diseño) facilitan optimización por gradiente.
- **Robustez:** pequeñas perturbaciones en entrada \(\Rightarrow\) pequeños cambios en salida (idealmente Lipschitz).

---

## 5. Enlaces directos

* **Teoría completa:** [sesion11.md](../teoria/sesion11.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 6. Nota

Funciones como **ReLU** son continuas; **derivabilidad** se trata en semanas posteriores (derivada en 0 de ReLU: subdiferencial).
