---
layout: default
---

# Fundamento matemático: notación, objetos y funciones en IA
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-01](../../../sesiones/sesion-01.md)

*(Alineado con la teoría de la Semana 1: [sesion1.md](../teoria/sesion1.md).)*

---

## 1. Notación y sumatorias

- **Índices y sucesiones:** \(x_1,\dots,x_n\); sucesión \(\{a_n\}\); serie \(\sum_{n=1}^\infty a_n\).
- **Sumatoria simple:** \(\sum_{i=1}^n x_i\); **doble:** \(\sum_i\sum_j a_{ij}\); **productoria:** \(\prod_{i=1}^n x_i\).

Estas expresiones aparecen en definiciones de pérdida (MSE, entropía), expectativas y normalizaciones.

---

## 2. Dimensiones y datos

- **2D / 3D / \(n\)D:** puntos \((x_1,\dots,x_n)\) como observaciones con \(n\) características.
- **Grafos** \(G=(V,E)\): nodos y aristas (dirigidas o no); base de GNN y recomendación.

---

## 3. Escalares, vectores, matrices y tensores

| Objeto | Notación típica | Rol en IA |
|--------|-----------------|------------|
| Escalar | \(a,\lambda\) | Hiperparámetro, learning rate |
| Vector | \(\mathbf{x}\in\mathbb{R}^n\) | Una muestra / embedding |
| Matriz | \(X,W\) | Dataset (filas=muestras), pesos de capa |
| Tensor orden \(k\) | \(\mathcal{T}\) | Lotes de imágenes, secuencias |

---

## 4. Funciones elementales

- **Lineal:** \(f(x)=mx+b\). **Polinomial,** **exp/log,** **trig** (\(\sin,\cos\)).
- **Hiperbólicas:** \(\tanh x=\frac{e^x-e^{-x}}{e^x+e^{-x}}\) (activaciones en RNN).

**Composición:** \(f\circ g\); una red profunda es composición de capas. **ReLU:** \(\max(0,x)\) (por tramos).

---

## 5. Activaciones y pérdidas (referencia)

- **Sigmoide:** \(\sigma(x)=\frac{1}{1+e^{-x}}\), \(\sigma'=\sigma(1-\sigma)\).
- **Pérdida (riesgo empírico):** \(L(\theta)=\frac{1}{n}\sum_i \ell(y_i,\hat y_i)\).
- **MSE:** \(\frac{1}{n}\sum_i (y_i-\hat y_i)^2\). **Log-loss** (binaria): combina logaritmos y sumas.

---

## 6. Enlaces directos

* **Teoría completa:** [sesion1.md](../teoria/sesion1.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Resumen de ecuaciones útiles

| Concepto | Expresión |
|----------|-----------|
| Media muestral | \(\bar x=\frac{1}{n}\sum_i x_i\) |
| MSE | \(\frac{1}{n}\sum_i (y_i-\hat y_i)^2\) |
| Entropía (discreta) | \(H=-\sum_i p_i\log p_i\) |
| Softmax (componente) | \(\hat y_k = e^{z_k}/\sum_j e^{z_j}\) |
