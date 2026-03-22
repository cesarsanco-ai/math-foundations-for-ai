---
layout: default
---

# Fundamento: probabilidad, estadística y decisiones bajo incertidumbre
#### Autor: Carlos César Sánchez Coronel

[⬅️ Volver a la Sesión-10](../../../sesiones/sesion-10.md)

*(Alineado con la teoría de la Semana 10: [sesion10.md](../teoria/sesion10.md).)*

---

## 1. Probabilidad básica

Axiomas; **condicional** \(P(A|B)=P(A\cap B)/P(B)\); **independencia** \(P(A\cap B)=P(A)P(B)\).

**Bayes:**

\[
P(A|B)=\frac{P(B|A)P(A)}{P(B)}
\]

(base de inferencia y Naive Bayes).

---

## 2. Variables aleatorias

**Esperanza** \(E[X]\); **varianza** \(\operatorname{Var}(X)=E[(X-E[X])^2]\); **covarianza** y **correlación** \(\rho\).

---

## 3. Distribuciones

**Normal** \(\mathcal{N}(\mu,\sigma^2)\); **Bernoulli / Binomial**; papel en ruido de modelos y regularización.

---

## 4. Entropía e información

\[
H(X)=-\sum_i p_i\log p_i
\]

(entropía cruzada como pérdida en clasificación).

---

## 5. Aplicaciones en IA

- **Naive Bayes,** HMM, **modelos generativos** (verosimilitudes).
- **Evaluación:** AUC como integración / orden de scores; **tests** A/B.

---

## 6. Enlaces directos

* **Teoría completa:** [sesion10.md](../teoria/sesion10.md)
* **CheatSheet:** [cheatsheet.md](../cheatsheet/cheatsheet.md)

---

## 7. Recordatorio Bayes en diagnóstico

**Prevalencia** baja + prueba buena puede dar \(P(\text{enfermo}|+)\) moderada (paradoja del falso positivo).
