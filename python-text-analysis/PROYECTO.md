# ✍️ Análisis de Texto y N-gramas | Marca Prima

Este proyecto de análisis de texto en Python se enfoca en desentrañar los insights clave de las conversaciones en torno a la marca **Prima** a través del procesamiento de lenguaje natural (NLP). El objetivo es identificar los temas y las asociaciones más frecuentes en los comentarios y mensajes alojados en redes sociales, prestando especial atención a los **bigramas** y el **sentimiento**.

---

## 🎯 Objetivo del Proyecto

-   **Descubrir insights:** Identificar los temas y las palabras/frases más relevantes en los datos textuales relacionados con la marca Prima.
-   **Análisis de sentimiento:** Explorar el sentimiento asociado a los comentarios, con un enfoque particular en el análisis de bigramas en textos negativos.
-   **Visualización de datos:** Utilizar nubes de palabras para representar visualmente la frecuencia de los bigramas y las asociaciones de términos.
-   **Validación de hipótesis:** Apoyar la toma de decisiones basada en datos cualitativos, complementando análisis cuantitativos.

---

## 🧪 Proceso de Desarrollo

Este proyecto sigue un flujo de trabajo estructurado para el análisis de texto:

### 1. Carga y Filtrado del Dataset
-   Carga de un dataset consolidado (`bbdd_consolidado_prima - quantico_sentimiento_prima.csv`).
-   Filtrado inicial para eliminar mensajes nulos y asegurar la consistencia de los IDs y formatos de fecha/hora.
-   Limpieza de caracteres especiales/codificación para un procesamiento correcto de los textos.

### 2. Preparación de Datos Textuales
-   Extracción de mensajes textuales relevantes, específicamente aquellos asociados a un sentimiento 'Negativo' para un análisis más profundo.
-   Obtención y aplicación de **stopwords en español** de la librería NLTK para eliminar palabras comunes que no aportan valor al análisis de frecuencia.

### 3. Análisis de N-gramas (Bigramas)
-   Utilización de `CountVectorizer` de Scikit-learn para extraer **bigramas (pares de palabras)** de los textos.
-   Cálculo de la frecuencia de aparición de cada bigrama.

### 4. Visualización con Nubes de Palabras (WordCloud)
-   Generación de nubes de palabras para representar la frecuencia de los bigramas.
-   Implementación de una función de color personalizada para resaltar los bigramas más frecuentes, permitiendo una identificación visual rápida de los temas dominantes en el sentimiento negativo.

---

## 🧱 Estructura del Dataset (Referencia)

El análisis se basa en un dataset que, según el código, contiene información de mensajes y su sentimiento asociado, entre otras columnas. Las columnas clave para este análisis son:

-   `mensaje`: Contiene el texto de los comentarios o interacciones.
-   `valoracion`: Indica el sentimiento asociado al mensaje (ej. 'Positiva', 'Negativa', 'Neutra').
-   `fecha`: Fecha de la interacción.
-   `hora`: Hora de la interacción.

📌 *Dado que el análisis se centra en un dataset específico y un proceso de script, no hay un "Modelo Dimensional" en el sentido de un dashboard de Power BI.*

---

## 📊 Resultados y Visualizaciones

A continuación, se presentan algunas de las visualizaciones generadas como parte de este análisis, que incluyen nubes de palabras enfocadas en los bigramas con sentimiento negativo:

### Nube de Palabras de Bigramas Negativos
Esta visualización resalta los pares de palabras más frecuentes en los mensajes con valoración negativa, con un esquema de colores que indica su frecuencia (rojo para más frecuente, amarillo para menos).

![Nube de Palabras de Bigramas Negativos](./nube_palabras_negativos.png)

*(Si tienes otras visualizaciones generadas por el script, como distribuciones de sentimiento o gráficos de frecuencia, puedes incluirlas aquí siguiendo el mismo formato de `![Descripción](./nombre_imagen.png)`).*

---

## 🧠 Insights y Conclusiones (Ejemplos)

Basado en el análisis de n-gramas, se pueden extraer conclusiones como:

-   [Aquí puedes añadir ejemplos de bigramas comunes en el sentimiento negativo y lo que podrían indicar. Por ejemplo: "servicio al cliente", "problema producto", "demora entrega".]
-   [Relaciona los bigramas con posibles áreas de mejora para la marca Prima.]
-   [Comenta si la nube de palabras reveló algún tema inesperado o recurrente.]
-   [Ejemplo: Los bigramas "servicio cliente" y "mala calidad" son recurrentes en los comentarios negativos, indicando áreas críticas de atención.]
-   [Ejemplo: La frecuencia de "demora entrega" sugiere un punto de fricción en la logística.]

---

## 🛠️ Herramientas Utilizadas

-   **Python:** Lenguaje de programación principal.
-   **Pandas:** Para manipulación y limpieza de datos.
-   **NLTK:** Para procesamiento de lenguaje natural (stopwords).
-   **Scikit-learn:** Para la vectorización y extracción de n-gramas (`CountVectorizer`).
-   **WordCloud:** Para la generación de nubes de palabras.
-   **Matplotlib, Seaborn:** Para visualización de datos.

---

## 📄 Archivos del Proyecto

-   `text_analysis.py`: Script principal de Python para el análisis de texto.
-   `bbdd_consolidado_prima - quantico_sentimiento_prima.csv`: (Archivo de datos, si lo incluyes en el repo o mencionas su ubicación).
-   `nube_palabras_negativos.png`: Imagen de la nube de palabras generada.

---

## 👤 Autor

Gabriel Rodríguez
[LinkedIn](https://www.linkedin.com/in/gabriel-rodr%C3%ADguez-4b4a6216b/)

---
