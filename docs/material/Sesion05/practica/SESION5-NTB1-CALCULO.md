---
layout: default
---
# Sesion 5: Ejercicios de Espacios Vectoriales y Normas

Material de práctica intermedio-avanzado orientado a IA. Cada ejercicio incluye desarrollo paso a paso y explicación aplicada.

## Ejercicios resueltos paso a paso

### Ejercicio 1: Base e independencia

**Enunciado (contexto IA):** Verifica si $v_1=(1,0,1), v_2=(0,1,1), v_3=(1,1,2)$ son LI.

**Solución paso a paso:**

1) Observa $v_3=v_1+v_2$.
2) Existe dependencia lineal.
3) No forman base de $\mathbb R^3$.
4) IA: features redundantes reducen información efectiva.

### Ejercicio 2: Producto punto y ángulo

**Enunciado (contexto IA):** Para $u=(1,2,2)$ y $v=(2,1,2)$ calcula coseno del ángulo.

**Solución paso a paso:**

1) $u\cdot v=1\cdot2+2\cdot1+2\cdot2=8$.
2) $||u||=||v||=3$.
3) $\cos\theta=8/9=0.8889$.
4) Alta similitud; útil en retrieval semántico.

### Ejercicio 3: Normas comparadas

**Enunciado (contexto IA):** En $x=(3,-4,1)$ calcula $||x||_1, ||x||_2, ||x||_\infty$.

**Solución paso a paso:**

1) $L1=3+4+1=8$.
2) $L2=\sqrt{9+16+1}=\sqrt{26}=5.099$.
3) $L\infty=4$.
4) Cada norma induce distinta geometría de regularización.

### Ejercicio 4: Distancia euclidiana

**Enunciado (contexto IA):** Distancia entre embeddings $a=(1,0,2)$ y $b=(2,-1,2)$.

**Solución paso a paso:**

1) Diferencia $a-b=(-1,1,0)$.
2) Norma: $\sqrt{1+1+0}=\sqrt2=1.414$.
3) Distancia pequeña => alta cercanía.
4) Base de KNN y clustering.

### Ejercicio 5: Distancia Manhattan

**Enunciado (contexto IA):** Con los mismos vectores, calcula distancia L1.

**Solución paso a paso:**

1) $|{-1}|+|1|+|0|=2$.
2) Penaliza linealmente desviaciones.
3) Más robusta a outliers que L2.
4) Útil en datos dispersos.

### Ejercicio 6: Proyección ortogonal

**Enunciado (contexto IA):** Proyecta $x=(3,4)$ sobre $u=(1,1)$.

**Solución paso a paso:**

1) $x\cdot u=7$, $u\cdot u=2$.
2) Coeficiente $=7/2=3.5$.
3) Proyección $=3.5(1,1)=(3.5,3.5)$.
4) IA: descomposición en subespacios.

### Ejercicio 7: Hiperplano SVM

**Enunciado (contexto IA):** Para $w=(2,-1)$ y $b=-3$, evalúa margen de $x=(2,1)$: $w\cdot x+b$.

**Solución paso a paso:**

1) $2(2)-1(1)-3=0$.
2) Punto cae en hiperplano de decisión.
3) Clasificador está indeciso.
4) SVM busca maximizar distancia al hiperplano.

### Ejercicio 8: Ridge penalización

**Enunciado (contexto IA):** Si $w=(1,-2,2)$ y $\lambda=0.1$, calcula penalidad L2.

**Solución paso a paso:**

1) $||w||_2^2=1+4+4=9$.
2) Penalidad $=0.1\cdot9=0.9$.
3) Reduce magnitud de pesos.
4) Mejora generalización.

### Ejercicio 9: Lasso penalización

**Enunciado (contexto IA):** Con el mismo $w$, penalidad L1 para $\lambda=0.1$.

**Solución paso a paso:**

1) $||w||_1=1+2+2=5$.
2) Penalidad $=0.5$.
3) Fomenta sparsidad (coeficientes cero).
4) Útil en selección de variables.

### Ejercicio 10: Coseno en embeddings

**Enunciado (contexto IA):** Si $q=(1,1,0)$ y $d=(2,0,0)$, calcula similitud coseno.

**Solución paso a paso:**

1) Producto: 2.
2) Normas: $||q||=\sqrt2$, $||d||=2$.
3) Coseno $=2/(2\sqrt2)=1/\sqrt2=0.7071$.
4) Moderada similitud semántica.
