---
layout: default
---
# Sesion 8: Ejercicios de Descomposicion de Matrices

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Identificar componentes SVD

**Enunciado (contexto IA):** En $A=U\Sigma V^T$, ¿qué representa cada factor?

**Solución paso a paso:**

1) $U$: base ortonormal de espacio columna.
2) $V$: base ortonormal de espacio fila.
3) $\Sigma$: escalas (valores singulares).
4) IA: separa dirección y magnitud de transformación.

### Ejercicio 2: Rango desde $\Sigma$

**Enunciado (contexto IA):** Si valores singulares son $(9,4,0,0)$, rango de $A$.

**Solución paso a paso:**

1) Cuenta valores singulares no nulos.
2) Hay 2 no nulos.
3) Rango=2.
4) Señala dimensionalidad efectiva de datos.

### Ejercicio 3: Compresión de bajo rango

**Enunciado (contexto IA):** Con singular values $(10,3,1)$, error espectral al truncar a rango 2.

**Solución paso a paso:**

1) Error en norma 2 = siguiente valor singular.
2) Error=$1$.
3) Buena compresión si cola pequeña.
4) IA: reduce memoria manteniendo señal principal.

### Ejercicio 4: Energía explicada

**Enunciado (contexto IA):** Con $(10,3,1)$, porcentaje energía primeros 2 (norma Frobenius).

**Solución paso a paso:**

1) Energía total $=10^2+3^2+1^2=110$.
2) Top2 $=100+9=109$.
3) Proporción $109/110=99.09\%$.
4) Justifica truncación agresiva.

### Ejercicio 5: Pseudoinversa escalar

**Enunciado (contexto IA):** Si $A=[2]$, calcula $A^+$.

**Solución paso a paso:**

1) Para escalar no nulo, pseudoinversa=recíproco.
2) $A^+=1/2$.
3) Verifica: $AA^+A=A$.
4) Base para mínimos cuadrados.

### Ejercicio 6: Solución mínima norma

**Enunciado (contexto IA):** Para sistema sobredeterminado, forma de solución LS.

**Solución paso a paso:**

1) Solución: $x=A^+b$.
2) Minimiza $||Ax-b||_2$.
3) Entre soluciones, da mínima norma.
4) IA: útil en ajuste lineal robusto.

### Ejercicio 7: LoRA bajo rango

**Enunciado (contexto IA):** Si $\Delta W=BA$ con $B\in\mathbb R^{d\times r}$, $A\in\mathbb R^{r\times k}$ y $r\ll d,k$, ventaja.

**Solución paso a paso:**

1) Parámetros pasan de $dk$ a $r(d+k)$.
2) Gran reducción de memoria.
3) Mantiene capacidad adaptativa focalizada.
4) IA: fine-tuning eficiente en LLMs.

### Ejercicio 8: Relación PCA-SVD

**Enunciado (contexto IA):** Para datos centrados $X$, ¿cómo obtener PCs con SVD?

**Solución paso a paso:**

1) Descompón $X=U\Sigma V^T$.
2) Columnas de $V$ son direcciones principales.
3) Varianzas proporcionales a $\Sigma^2/(n-1)$.
4) Método numéricamente estable.

### Ejercicio 9: Reconstrucción aproximada

**Enunciado (contexto IA):** Si $A_k=U_k\Sigma_kV_k^T$, objetivo de k pequeño.

**Solución paso a paso:**

1) Minimiza error entre matrices de rango k.
2) Teorema Eckart-Young garantiza óptimo.
3) Conserva estructura dominante.
4) IA: compresión de embeddings/modelos.

### Ejercicio 10: Costo computacional SVD

**Enunciado (contexto IA):** ¿Por qué SVD completa puede ser costosa en matrices gigantes?

**Solución paso a paso:**

1) Costo cúbico aproximado en dimensión.
2) Memoria elevada para guardar factores completos.
3) Se usan SVD truncada/aleatoria.
4) Escalable para sistemas reales de IA.
