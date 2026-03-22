---
layout: default
---

# Fundamento: modelo, pérdida y optimización en IA
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-02](../../../sesiones/sesion-02.md)

*(Alineado con la teoría de la Semana 2: [sesion2.md](../teoria/sesion2.md).)*

---

## 1. Definiciones de IA y tipos de aprendizaje

- **IA estrecha:** tareas concretas; **IA general:** aún teórica.
- **Supervisado:** datos \((x_i,y_i)\); **no supervisado:** solo \(x_i\); **refuerzo:** recompensas del entorno.

---

## 2. Tres componentes de todo modelo

1. **Predicción:** \(\hat y = f(x;\theta)\).
2. **Pérdida:** \(L(\theta)=\frac{1}{n}\sum_i \ell(y_i,f(x_i;\theta))\).
3. **Optimización:** \(\min_\theta L(\theta)\).

Esta estructura es **minimización del riesgo empírico (ERM)**.

---

## 3. Pérdidas por tipo de problema

- **Regresión:** MSE, MAE; **clustering (k-means):** SSE \(\sum_k\sum_{x\in C_k}\|x-\mu_k\|^2\).
- **Clasificación:** log-loss binaria y multiclase con softmax.
- **SVM:** hinge \(\max(0, 1-y\,\hat y)\) con \(y\in\{-1,1\}\).

---

## 4. Optimización

- **Cerrada:** p. ej. \(\theta=(X^\top X)^{-1}X^\top y\) (OLS).
- **Iterativa:** \(\theta \leftarrow \theta - \eta \nabla L(\theta)\) (gradiente); **SGD** con mini-batches; **Adam** en deep learning.
- **Regularización:** \(L(\theta)=\text{Loss}+\lambda R(\theta)\) (Ridge: \(\|\theta\|_2^2\)).

---

## 5. ML vs DL

- **ML clásico:** muchas formulaciones convexas o algoritmos especializados.
- **DL:** pérdidas no convexas; **backprop** = regla de la cadena en grafo de cómputo.

---

## 6. Enlaces directos

* **Teoría completa:** [sesion2.md](../teoria/sesion2.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Tabla unificada

| Elemento | Pregunta que responde |
|----------|------------------------|
| Modelo \(f\) | ¿Qué familia de funciones? |
| Pérdida \(\ell\) | ¿Qué es equivocarse? |
| Optimizador | ¿Cómo actualizar \(\theta\)? |
