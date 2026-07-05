# FDS-2026-1-16685

# FDS-2026-1-16685

## Objetivo del proyecto

Analizar el conjunto de datos **Trending YouTube Video Statistics**, correspondiente a videos en tendencia de YouTube en Gran Bretaña, con el fin de identificar patrones relacionados con las visualizaciones, los likes, los comentarios, las categorías y los canales de mayor impacto.

El proyecto sigue la metodología **CRISP-DM**, abarcando la comprensión del negocio, la comprensión de los datos, la preparación de los datos, el análisis exploratorio y la evaluación preliminar de relaciones entre variables.

## Integrantes

| Integrante | Código | Rol |
|---|---:|---|
| Cordova Montenegro, Sebastian | U202321420 | Business Project Sponsor |
| Parra Flores, Franco Andre | U202322315 | Data Engineer |
| Becerra Salas, Joaquín Estuardo | U20231f717 | Data Scientist |

## Descripción del conjunto de datos

El dataset contiene **38 916 registros** y variables asociadas a videos de YouTube en tendencia de Gran Bretaña. Entre las principales columnas se encuentran:

- `video_id`: identificador del video.
- `title`: título del video.
- `channel_title`: canal que publicó el video.
- `category_id`: identificador numérico de la categoría.
- `views`: cantidad de visualizaciones.
- `likes`: cantidad de Me gusta.
- `dislikes`: cantidad de No me gusta.
- `comment_count`: cantidad de comentarios.
- `description`: descripción del video.

Además, se utilizó el archivo `GB_category_id.json` para asociar cada identificador de categoría con su nombre correspondiente mediante la variable `category_name`.

También se generó la variable derivada `ratio_likes`, calculada mediante la siguiente expresión:

`ratio_likes = likes / (dislikes + 1)`

Se añadió una unidad al denominador para evitar divisiones entre cero en aquellos videos que no presentan dislikes.

## Metodología CRISP-DM

### 1. Comprensión del negocio

Se busca comprender qué factores están asociados al rendimiento de los videos en tendencia de YouTube en Gran Bretaña, considerando métricas de interacción, categorías de contenido y canales con mayor impacto.

La variable principal de análisis es `views`, que representa la cantidad de visualizaciones obtenidas por cada video.

Entre las principales variables consideradas para el análisis se encuentran:

- `likes`: cantidad de Me gusta recibidos por el video.
- `comment_count`: cantidad de comentarios realizados por los usuarios.
- `category_name`: categoría a la que pertenece el video.
- `ratio_likes`: relación derivada entre likes y dislikes.

### 2. Comprensión de los datos

Se realizó una exploración inicial del conjunto de datos con el propósito de conocer su estructura y evaluar la calidad de la información disponible.

Durante esta etapa se analizaron:

- Dimensiones del dataset.
- Tipos de variables.
- Nombres de columnas.
- Estadísticas descriptivas.
- Cantidad de valores únicos.
- Presencia de valores nulos.
- Existencia de registros duplicados.
- Correlación entre las principales variables numéricas.

### 3. Preparación de los datos

Se realizaron las siguientes tareas:

- Carga del archivo CSV inicial.
- Carga del archivo JSON de categorías.
- Creación de un diccionario de categorías a partir del archivo JSON.
- Asociación de `category_id` con el nombre correspondiente de cada categoría.
- Creación de la variable `category_name`.
- Reemplazo de categorías no encontradas por `No clasificada`.
- Tratamiento de valores faltantes en `description`.
- Creación de la variable derivada `ratio_likes = likes / (dislikes + 1)`.
- Generación del dataset limpio y preparado para análisis.

El proceso permitió conservar los registros originales y enriquecer el conjunto de datos con nuevas variables útiles para el análisis.

### 4. Análisis exploratorio de datos

Se desarrollaron visualizaciones orientadas a analizar el comportamiento de los videos en tendencia y responder preguntas relevantes del proyecto.

Entre los análisis realizados se encuentran:

- Top 10 canales con mayor número de visualizaciones.
- Correlación entre variables numéricas.
- Cantidad de videos por categoría.
- Visualizaciones totales por categoría.
- Top 10 videos con mayor número de visualizaciones.
- Likes acumulados por categoría.
- Promedio de visualizaciones por categoría.
- Top 10 canales con mayor cantidad de likes.
- Promedio de likes por video según categoría.
- Relación entre `likes` y `views`.

### 5. Evaluación preliminar para la selección de una técnica de modelado

Debido a que `views` es una variable numérica, se consideró la **Regresión Lineal** como una posible técnica para analizar la relación entre las visualizaciones y las variables de interacción del conjunto de datos.

Como parte del análisis preliminar, se estudió gráficamente la relación entre `likes` y `views` mediante un diagrama de dispersión.

Para facilitar la visualización del comportamiento de los datos, se utilizó una muestra aleatoria de **3000 registros** con `random_state=42`, permitiendo mantener la reproducibilidad del análisis.

El gráfico permitió identificar una tendencia positiva entre ambas variables. Sin embargo, la dispersión observada muestra que la relación no es completamente lineal y sugiere que otros factores también influyen en el comportamiento de las visualizaciones.

Este análisis constituye una evaluación exploratoria orientada a sustentar la selección de una posible técnica de modelado dentro de la propuesta basada en la metodología CRISP-DM.

## Principales conclusiones

- La categoría **Music** concentra la mayor cantidad de videos en tendencia y también el mayor volumen de visualizaciones.
- Los canales con mayor popularidad acumulan una parte importante de las visualizaciones y los likes.
- El análisis exploratorio muestra una tendencia positiva entre `likes` y `views`.
- La dispersión observada indica que el rendimiento de los videos no depende únicamente de una métrica de interacción.
- El análisis de dispersión entre `likes` y `views` permitió identificar una relación positiva, aunque la variabilidad observada indica que deben considerarse otros factores para explicar el comportamiento de las visualizaciones.

## Licencia de uso

Este proyecto se publica con fines académicos bajo la licencia **MIT**. El dataset original pertenece a sus respectivos autores y se utiliza únicamente con fines educativos.
