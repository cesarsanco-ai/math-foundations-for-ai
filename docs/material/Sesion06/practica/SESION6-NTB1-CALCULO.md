---
layout: default
---
# Sesión 6: Transformaciones Lineales - Solucionario NTB1

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Matriz de transformación

**Enunciado (contexto IA):** Para $T(x,y)=(3x+y,2y)$, halla su matriz.

**Solución paso a paso:**

1) $T(e_1)=(3,0)$, $T(e_2)=(1,2)$.
2) Matriz: $A=\begin{pmatrix}3&1\\0&2\end{pmatrix}$.
3) Verifica: $A(x,y)^T=(3x+y,2y)^T$.
4) IA: capa lineal en red neuronal.

### Ejercicio 2: Composición de capas

**Enunciado (contexto IA):** Con $A=\begin{pmatrix}1&1\\0&1\end{pmatrix}$ y $B=\begin{pmatrix}2&0\\0&2\end{pmatrix}$ calcula $BA$.

**Solución paso a paso:**

1) Multiplica: $BA=\begin{pmatrix}2&2\\0&2\end{pmatrix}$.
2) Primero A luego escalado B.
3) Redes profundas componen transformaciones.
4) El orden importa.

### Ejercicio 3: Linealidad

**Enunciado (contexto IA):** ¿$T(x,y)=(x+y+1,y)$ es lineal?

**Solución paso a paso:**

1) Evalúa en origen: $T(0,0)=(1,0)$.
2) No preserva origen.
3) Entonces no es lineal (afín).
4) En IA esto sería capa con sesgo explícito.

### Ejercicio 4: Núcleo e imagen

**Enunciado (contexto IA):** Para $T(x,y)=(x-y,0)$ encuentra ker e Im.

**Solución paso a paso:**

1) ker: $x-y=0\Rightarrow(x,x)$.
2) Im: vectores $(t,0)$.
3) dim ker=1, rango=1.
4) Teorema rango-nulidad: 2=1+1.

### Ejercicio 5: Escalado de features

**Enunciado (contexto IA):** Transforma $x=(2,-3)$ con $A=\text{diag}(0.5,2)$.

**Solución paso a paso:**

1) Multiplica: $(1,-6)$.
2) Primera feature reduce escala, segunda amplifica.
3) Similar a normalización anisotrópica.
4) Impacta gradientes y convergencia.

### Ejercicio 6: Rotación 90°

**Enunciado (contexto IA):** Aplica $R=\begin{pmatrix}0&-1\\1&0\end{pmatrix}$ a $x=(3,1)$.

**Solución paso a paso:**

1) $Rx=(-1,3)$.
2) Longitud se conserva.
3) Rotaciones son ortogonales.
4) En visión, data augmentation geométrica.

### Ejercicio 7: Proyección

**Enunciado (contexto IA):** Con $P=\begin{pmatrix}1&0\\0&0\end{pmatrix}$ proyecta $(4,5)$.

**Solución paso a paso:**

1) $P(4,5)=(4,0)$.
2) Elimina segunda componente.
3) Es idempotente: $P^2=P$.
4) Similar a seleccionar subespacio de features.

### Ejercicio 8: Rango de una capa

**Enunciado (contexto IA):** Si $W$ de una capa es $3\times5$, rango máximo.

**Solución paso a paso:**

1) Rango $\le\min(3,5)=3$.
2) La salida vive en subespacio de dimensión como mucho 3.
3) Limita capacidad lineal.
4) Motiva overparameterization en DL.

### Ejercicio 9: Cambio de base

**Enunciado (contexto IA):** Si $x_B=(2,1)$ y base $B=\{(1,1),(1,-1)\}$, halla coordenada estándar.

**Solución paso a paso:**

1) Combina: $2(1,1)+1(1,-1)=(3,1)$.
2) Vector estándar $(3,1)$.
3) Distintas bases facilitan análisis.
4) En IA, PCA cambia base a componentes principales.

### Ejercicio 10: Transformación en batch

**Enunciado (contexto IA):** Si $X$ es $4\times3$ y $W$ es $3\times2$, dimensión de $XW$.

**Solución paso a paso:**

1) Producto válido porque 3=3.
2) Resultado $4\times2$.
3) 4 muestras, 2 nuevas features.
4) Patrón típico en capas densas.
