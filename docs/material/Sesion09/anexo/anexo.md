---
layout: default
---

# Fundamento: tensores, broadcasting y representación de datos
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-09](../../../sesiones/sesion-09.md)

*(Alineado con la teoría de la Semana 9: [sesion9.md](../teoria/sesion9.md).)*

---

## 1. Definiciones

**Tensor:** arreglo multidimensional; **orden (rank)** = número de ejes; **shape** = tupla de tamaños.

| Orden | Ejemplo |
|-------|---------|
| 0 | Escalar |
| 1 | Vector \((n,)\) |
| 2 | Matriz \((m,n)\) |
| 3+ | Imagen \((H,W,C)\), lote \((B,H,W,C)\) |

---

## 2. Datos en IA

- **Imagen:** \((H,W)\) o \((H,W,3)\); **lote** \(B\) como primer eje.
- **Secuencia:** \((B,T,F)\) batch × tiempo × features; **texto** con embeddings \((B,L,D)\).

---

## 3. Operaciones

- Suma/ producto **Hadamard** (misma shape).
- **Contracción** / producto matricial como caso particular.
- **Broadcasting:** alinear dimensiones desde la última; tamaño 1 o ausente se expande.

---

## 4. Reorganización

**reshape,** **transpose** (permute de ejes), **flatten** para capas densas.

---

## 5. Enlaces directos

* **Teoría completa:** [sesion9.md](../teoria/sesion9.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 6. Frameworks

PyTorch: **NCHW** vs NumPy **NHWC**; siempre verificar orden de `permute`/`contiguous`.
