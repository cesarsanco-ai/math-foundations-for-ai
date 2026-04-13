---
layout: default
---
# Sesion 9: Ejercicios de Tensores

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Shape en visión

**Enunciado (contexto IA):** Batch de 16 imágenes RGB 128x128 en formato NHWC. shape?

**Solución paso a paso:**

1) N=batch=16.
2) H=128, W=128, C=3.
3) Shape $(16,128,128,3)$.
4) Estructura estándar en pipelines de CV.

### Ejercicio 2: Broadcasting suma

**Enunciado (contexto IA):** Suma tensor $X(2,3)$ con bias $b(3,)$. ¿shape final?

**Solución paso a paso:**

1) $b$ se expande por eje batch.
2) Operación válida por reglas broadcasting.
3) Resultado $(2,3)$.
4) IA: usado en capas densas y normalización.

### Ejercicio 3: Reshape consistente

**Enunciado (contexto IA):** Convierte tensor $(4,5,6)$ a matriz 2D para capa lineal.

**Solución paso a paso:**

1) Elementos totales: $4\cdot5\cdot6=120$.
2) Opción común: $(4,30)$.
3) Mantiene conteo de elementos.
4) Flatten previo a MLP.

### Ejercicio 4: Transpose en atención

**Enunciado (contexto IA):** Tensor de atención $(batch,heads,seq,dim)=(8,12,20,64)$. permuta a $(8,20,12,64)$.

**Solución paso a paso:**

1) Intercambia ejes heads y seq.
2) Nuevo shape $(8,20,12,64)$.
3) No cambia datos, solo vista/orden.
4) Necesario para ciertas implementaciones.

### Ejercicio 5: Squeeze/unsqueeze

**Enunciado (contexto IA):** Aplica squeeze a $(1,32,1,128)$ y luego unsqueeze en eje 0.

**Solución paso a paso:**

1) squeeze elimina dimensiones 1: $(32,128)$.
2) unsqueeze eje 0: $(1,32,128)$.
3) Control de batch explícito.
4) Frecuente en inferencia single-sample.

### Ejercicio 6: Reducción por eje

**Enunciado (contexto IA):** Si $X$ tiene shape $(10,50)$, media por eje 0 y eje 1 shapes?

**Solución paso a paso:**

1) Eje0 (columnas): shape $(50,)$.
2) Eje1 (filas): shape $(10,)$.
3) Diferente semántica estadística.
4) IA: pooling y agregación.

### Ejercicio 7: Producto Hadamard

**Enunciado (contexto IA):** Con $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$, $B=\begin{pmatrix}2&0\\1&5\end{pmatrix}$ calcula $A\odot B$.

**Solución paso a paso:**

1) Multiplica elemento a elemento.
2) Resultado $\begin{pmatrix}2&0\\3&20\end{pmatrix}$.
3) No confundir con producto matricial.
4) Usado en puertas de LSTM y máscaras.

### Ejercicio 8: einsum interpretación

**Enunciado (contexto IA):** Interpreta `ij,jk->ik`.

**Solución paso a paso:**

1) Indice j se contrae (suma).
2) Resultado índices i,k.
3) Equivale a multiplicación de matrices.
4) Notación compacta para operaciones complejas.

### Ejercicio 9: Memoria tensor

**Enunciado (contexto IA):** float32 usa 4 bytes. Cuánta memoria ocupa tensor $(64,512,768)$?

**Solución paso a paso:**

1) Elementos: $64\cdot512\cdot768=25,165,824$.
2) Bytes: $100,663,296$.
3) En MB: $\approx96$ MiB.
4) IA: crítico para dimensionar GPU.

### Ejercicio 10: Masking en NLP

**Enunciado (contexto IA):** Secuencia padded a longitud 6 con máscara [1,1,1,0,0,0]. utilidad.

**Solución paso a paso:**

1) Máscara evita atención/pérdida sobre padding.
2) Mantiene gradientes en tokens reales.
3) Mejora estabilidad de entrenamiento.
4) Esencial en modelos de lenguaje.
