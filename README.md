# FDS-2026-1-16685

## Objetivo del proyecto

Analizar el conjunto de datos **Trending YouTube Video Statistics**, correspondiente a videos en tendencia de YouTube en Gran Bretaña, con el fin de identificar patrones relacionados con las visualizaciones, los likes, los comentarios, las categorías y los canales de mayor impacto.

El proyecto sigue la metodología **CRISP-DM**, abarcando la comprensión del negocio, comprensión de los datos, preparación de los datos, análisis exploratorio y una aproximación inicial al modelado.

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

Además, se utilizó el archivo `GB_category_id.json` para asociar cada identificador de categoría con su nombre correspondiente mediante la variable `category_name`. También se generó la variable derivada `ratio_likes`.

## Metodología CRISP-DM

### 1. Comprensión del negocio

Se busca comprender qué factores están asociados al rendimiento de los videos en tendencia de YouTube en Gran Bretaña, considerando métricas de interacción, categorías de contenido y canales con mayor impacto.

### 2. Comprensión de los datos

Se inspeccionó la estructura del dataset, los tipos de variables, la cantidad de valores únicos, la presencia de valores nulos, los registros duplicados y las estadísticas descriptivas de las principales variables numéricas.

### 3. Preparación de los datos

Se realizaron las siguientes tareas:

- Carga del archivo CSV inicial.
- Carga del archivo JSON de categorías.
- Creación de la variable `category_name`.
- Reemplazo de valores nulos en `description` por `Sin descripción`.
- Reemplazo de categorías no encontradas por `No clasificada`.
- Creación de la variable `ratio_likes = likes / (dislikes + 1)`.
- Exportación del dataset limpio y preparado para análisis.

### 4. Análisis exploratorio

Se desarrollaron visualizaciones orientadas a analizar:

- Cantidad de videos por categoría.
- Visualizaciones totales por categoría.
- Canales con mayor número de visualizaciones.
- Videos con mayor número de visualizaciones.
- Likes acumulados por categoría.
- Promedio de visualizaciones por categoría.
- Canales con mayor cantidad de likes.
- Relación entre `likes` y `views`.

### 5. Aproximación inicial al modelado y evaluación

Debido a que `views` es una variable numérica, se seleccionó la **Regresión Lineal** como técnica candidata para una futura etapa de modelado predictivo.

Como evaluación preliminar, se analizó gráficamente la relación entre `likes` y `views` mediante un diagrama de dispersión. Para facilitar la visualización, se utilizó una muestra aleatoria de 3000 registros con `random_state=42`.

El análisis permitió identificar una tendencia positiva entre ambas variables. Sin embargo, la dispersión observada evidencia que la relación no es completamente lineal y que otros factores también influyen en el comportamiento de las visualizaciones.

En esta etapa no se entrenó un modelo predictivo de Regresión Lineal ni se calcularon métricas como R², RMSE o MAE.

## Principales conclusiones

- La categoría **Music** concentra la mayor cantidad de videos en tendencia y también el mayor volumen de visualizaciones.
- Los canales con mayor popularidad acumulan una parte importante de las visualizaciones y los likes.
- El análisis exploratorio muestra una tendencia positiva entre `likes` y `views`.
- La dispersión observada indica que el rendimiento de los videos no depende únicamente de una métrica de interacción.
- La Regresión Lineal constituye una técnica candidata para una futura etapa de modelado predictivo, en la que deberán incorporarse métricas de evaluación como R², RMSE y MAE.

## Licencia de uso

Este proyecto se publica con fines académicos bajo la licencia **MIT**. El dataset original pertenece a sus respectivos autores y se utiliza únicamente con fines educativos.
