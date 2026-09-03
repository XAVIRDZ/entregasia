# Actividad 7: Evaluación del Clasificador Naive Bayes con Matriz de Confusión (Iris)

- **Autor:** Xavi Rdz
- **Dataset:** Iris Dataset (150 observaciones, 4 atributos continuos)
- **Archivo de trabajo:** `./naive-byes.iris.data.xls`
  - Observaciones originales: Celdas `[A1:F150]`
  - Tabulación y fórmulas Naive Bayes: Celdas `[T151:AC413]`

---

## 1. Fundamentos Teóricos del Modelo

El clasificador **Naive Bayes (NB)** es un modelo probabilístico supervisado fundamentado en el **Teorema de Bayes**:

$$P(C_k \mid \mathbf{x}) = \frac{P(C_k) \cdot P(\mathbf{x} \mid C_k)}{P(\mathbf{x})}$$

Donde:
- $P(C_k)$ representa la **probabilidad a priori** de cada especie (en un conjunto balanceado con 50 instancias por clase, $P(C_k) = \frac{50}{150} = \frac{1}{3} \approx 0.3333$).
- $P(\mathbf{x} \mid C_k)$ es la **verosimilitud** de los atributos observados condicionados a la clase $C_k$.
- Se aplica la suposición de **independencia condicional** (*Naive*), asumiendo que los cuatro atributos biométricos son independientes entre sí dada la clase:

$$P(\mathbf{x} \mid C_k) = \prod_{i=1}^{4} P(x_i \mid C_k)$$

### Tratamiento de Variables Continuas (Modelo Gaussiano)
Debido a que las variables biométricas (*Sepal.Length*, *Sepal.Width*, *Petal.Length*, *Petal.Width*) son continuas, el archivo Excel modela cada una mediante una **función de densidad de probabilidad normal (gaussiana)** a partir de la media ($\mu$) y la desviación estándar ($\sigma$) calculadas por clase:

$$P(x_i \mid C_k) = \frac{1}{\sqrt{2\pi\sigma_k^2}} \exp\left( -\frac{(x_i - \mu_k)^2}{2\sigma_k^2} \right)$$

Para asignar la clase final, el clasificador evalúa cuál de las tres especies maximiza el producto $P(C_k) \prod P(x_i \mid C_k)$ (criterio *Maximum A Posteriori* - MAP).

---

## 2. Metodología de Muestreo y Evaluación

1. **Origen de los datos:** En el rango `[A1:F150]` se localizan los 150 registros originales con sus 4 atributos biométricos y la columna de clase real (`setosa`, `versicolor`, `virginica`).
2. **Tabulación de resultados:** En el rango `[T151:AC413]` del archivo Excel se encuentran tabuladas las densidades calculadas y la etiqueta asignada por el clasificador para cada fila.
3. **Muestreo aleatorio:** Para realizar una evaluación insesgada, se seleccionaron de forma aleatoria 20 observaciones sin repetición del total de 150 filas.

---

## 3. Registro de las 20 Observaciones Seleccionadas

A continuación se detalla cada una de las 20 observaciones muestreadas, contrastando sus valores biométricos, la clase real registrada en `[A1:F150]` y la predicción generada en el bloque `[T151:AC413]`:

| N° | Fila Excel (`A1:F150`) | Longitud Sépalo | Ancho Sépalo | Longitud Pétalo | Ancho Pétalo | Especie Real | Predicción NB (`T151:AC413`) | ¿Acierto? |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | **Fila 2**   | 4.9 | 3.0 | 1.4 | 0.2 | **setosa**     | **setosa**     | Sí |
| 2 | **Fila 11**  | 5.4 | 3.7 | 1.5 | 0.2 | **setosa**     | **setosa**     | Sí |
| 3 | **Fila 20**  | 5.1 | 3.8 | 1.5 | 0.3 | **setosa**     | **setosa**     | Sí |
| 4 | **Fila 22**  | 5.1 | 3.7 | 1.5 | 0.4 | **setosa**     | **setosa**     | Sí |
| 5 | **Fila 36**  | 5.0 | 3.2 | 1.2 | 0.2 | **setosa**     | **setosa**     | Sí |
| 6 | **Fila 39**  | 4.4 | 3.0 | 1.3 | 0.2 | **setosa**     | **setosa**     | Sí |
| 7 | **Fila 40**  | 5.1 | 3.4 | 1.5 | 0.2 | **setosa**     | **setosa**     | Sí |
| 8 | **Fila 50**  | 5.0 | 3.3 | 1.4 | 0.2 | **setosa**     | **setosa**     | Sí |
| 9 | **Fila 54**  | 5.5 | 2.3 | 4.0 | 1.3 | **versicolor** | **versicolor** | Sí |
| 10| **Fila 56**  | 5.7 | 2.8 | 4.5 | 1.3 | **versicolor** | **versicolor** | Sí |
| 11| **Fila 61**  | 5.0 | 2.0 | 3.5 | 1.0 | **versicolor** | **versicolor** | Sí |
| 12| **Fila 67**  | 5.6 | 3.0 | 4.5 | 1.5 | **versicolor** | **versicolor** | Sí |
| 13| **Fila 68**  | 5.8 | 2.7 | 4.1 | 1.0 | **versicolor** | **versicolor** | Sí |
| 14| **Fila 73**  | 6.3 | 2.5 | 4.9 | 1.5 | **versicolor** | **versicolor** | Sí |
| 15| **Fila 86**  | 6.0 | 3.4 | 4.5 | 1.6 | **versicolor** | **versicolor** | Sí |
| 16| **Fila 88**  | 6.3 | 2.3 | 4.4 | 1.3 | **versicolor** | **versicolor** | Sí |
| 17| **Fila 92**  | 6.1 | 3.0 | 4.6 | 1.4 | **versicolor** | **versicolor** | Sí |
| 18| **Fila 112** | 6.4 | 2.7 | 5.3 | 1.9 | **virginica**  | **virginica**  | Sí |
| 19| **Fila 113** | 6.8 | 3.0 | 5.5 | 2.1 | **virginica**  | **virginica**  | Sí |
| 20| **Fila 143** | 5.8 | 2.7 | 5.1 | 1.9 | **virginica**  | **virginica**  | Sí |

---

## 4. Construcción de la Matriz de Confusión (3x3)

### Regla de Mapeo
- **Filas:** Etiqueta predicha por el clasificador Naive Bayes.
- **Columnas:** Etiqueta real de la observación.
- **Orden especificado:** `setosa`, `virginica`, `versicolor`.

Cada observación se clasifica en una celda $(i, j)$ correspondiente a `(Fila Predicha, Columna Real)`:

| Clasificador\ Valor Real | **setosa** | **virginica** | **versicolor** | **Total Clasificado** |
|:---                      |:---:       |:---:          |:---:           |:---:                  |
| **setosa**               | 8          | 0             | 0              | **8**                 |
| **virginica**            | 0          |3              | 0              | **3**                 |
| **versicolor**           | 0          | 0             | **9**          | **9**                 |
| **Total Real**           | 8          | 3             | **9**          | **20**                |


## 5. Explicación e Interpretación de los Resultados

### Análisis Celda por Celda:
1. **Fila `setosa`:**
   - Columna `setosa`: **8**. Hubo 8 instancias que eran realmente *setosa* y el clasificador las predijo como *setosa* (verdaderos positivos de *setosa*).
   - Columnas `virginica` y `versicolor`: **0**. Ninguna flor de otra especie fue erróneamente clasificada como *setosa*.
2. **Fila `virginica`:**
   - Columna `virginica`: **3**. Las 3 instancias reales de *virginica* fueron identificadas correctamente.
   - Columnas `setosa` y `versicolor`: **0**. No se registraron falsos positivos hacia *virginica*.
3. **Fila `versicolor`:**
   - Columna `versicolor`: **9**. Las 9 instancias reales de *versicolor* se clasificaron correctamente.
   - Columnas `setosa` y `virginica`: **0**. No hubo confusiones provenientes de otras especies.

### Métricas de Rendimiento:
- **Total de observaciones evaluadas ($N$):** 20
- **Clasificaciones correctas (Diagonal Principal):** $8 + 3 + 9 = 20$
- **Clasificaciones erróneas:** 0
- **Exactitud (Accuracy):**
  $$\text{Accuracy} = \frac{\sum \text{Aciertos}}{N} = \frac{20}{20} = 1.0 \; (100\%)$$

### Conclusión Técnica:
El clasificador Naive Bayes demuestra un desempeño robusto sobre la muestra seleccionada. Las flores de tipo *setosa* quedan completamente aisladas de las otras clases gracias a la reducida magnitud de sus pétalos ($<2.0\text{ cm}$). Por su parte, la densidad gaussiana estimada en los parámetros de *versicolor* y *virginica* permitió asignar probabilidades a posteriori dominantes en la clase correcta para todas las muestras evaluadas en este subconjunto.