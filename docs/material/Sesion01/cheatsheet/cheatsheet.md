---
layout: default
---

# Cheatsheet: Fundamentos matemáticos
**Autor:** Carlos César Sánchez Coronel  

[⬅️ Volver a la Sesión-01](../../../sesiones/sesion-01.md)

---

## Notación

| Símbolo | Uso |
| :--- | :--- |
| \(\sum_{i=1}^n\) | Sumar términos indexados |
| \(\prod_{i=1}^n\) | Producto |
| \(\mathbb{R}^n\) | Espacio de vectores \(n\)-dimensionales |

---

## Objetos en código / IA

| Orden | Ejemplo | Shape típico |
| :--- | :--- | :--- |
| 0 | Escalar | `()` |
| 1 | Vector feature | `(n,)` |
| 2 | Matriz datos / pesos | `(n_samples, n_features)` |
| \(\geq 3\) | Imagen, lote, video | `(B,H,W,C)` etc. |

---

## Activaciones frecuentes

| Función | Fórmula | Rango / nota |
| :--- | :--- | :--- |
| **Sigmoide** | \(1/(1+e^{-x})\) | \((0,1)\), probabilidades |
| **tanh** | \((e^x-e^{-x})/(e^x+e^{-x})\) | \((-1,1)\) |
| **ReLU** | \(\max(0,x)\) | estándar en CNN/MLP |

---

## Pérdidas (recordatorio)

| Tarea | Pérdida | Idea |
| :--- | :--- | :--- |
| Regresión | MSE | Penaliza errores grandes |
| Clasificación | Cross-entropy | Alinea \(\hat p\) con etiqueta |
| Robustez | MAE | Menos sensible a outliers |

---

## Python mínimo (NumPy)

```python
import numpy as np
x = np.array([1., 2., 3.])
y = np.sum(x ** 2)          # sumatoria
z = np.exp(x) / np.exp(x).sum()  # softmax 1D
```

---

## Puntos críticos

* **Composición** de funciones = arquitectura en profundidad; la **regla de la cadena** conecta con el gradiente.
* Unificar **notación** (vectores columna, bias explícito) evita errores en \(\mathbf{y}=X\boldsymbol{\theta}\).

> *“Escalar → vector → matriz → tensor es la misma idea: datos con más ejes.”*
