# FDS-2026-1-16685

## Objetivo del proyecto

Analizar el conjunto de datos **Trending YouTube Video Statistics** correspondiente a videos en tendencia de YouTube en Gran Bretaña, con el fin de identificar patrones relacionados con visualizaciones, likes, comentarios, categorías y canales de mayor impacto.

El proyecto sigue la metodología **CRISP-DM**, abarcando comprensión del negocio, comprensión de los datos, preparación, análisis exploratorio, modelado inicial y evaluación de resultados.

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

Además, se utilizó el archivo `GB_category_id.json` para crear la variable `category_name`, y se generó la variable derivada `ratio_likes`.

## Estructura del repositorio

```text
FDS-2026-1-16685/
├── data/
│   ├── GBvideos_cc50_202101.csv
│   ├── GB_category_id.json
│   └── GBvideos_limpio_preparado.csv
├── code/
│   └── upc_2026_01_16685_03_tf_final.ipynb
├── README.md
├── requirements.txt
└── LICENSE
```

## Metodología CRISP-DM

### 1. Comprensión del negocio
Se busca comprender qué factores están asociados al rendimiento de los videos en tendencia de YouTube en Gran Bretaña.

### 2. Comprensión de los datos
Se inspeccionó la estructura del dataset, los tipos de variables, valores nulos, valores únicos, duplicados y estadísticas descriptivas.

### 3. Preparación de los datos
Se realizaron las siguientes tareas:

- Carga del archivo CSV inicial.
- Carga del archivo JSON de categorías.
- Creación de la variable `category_name`.
- Reemplazo de valores nulos en `description` por `Sin descripcion`.
- Reemplazo de categorías no encontradas por `No clasificada`.
- Creación de la variable `ratio_likes = likes / (dislikes + 1)`.
- Exportación del dataset limpio y preparado.

### 4. Modelado y evaluación
Se aplicó un modelo inicial de **Regresión Lineal** para analizar el comportamiento de `views` a partir de variables como `likes`, `comment_count` y `ratio_likes`.

## Principales conclusiones

- La categoría **Music** concentra la mayor cantidad de videos en tendencia y también el mayor volumen de visualizaciones.
- Los canales con mayor popularidad acumulan una parte importante de las visualizaciones y los likes.
- La variable `likes` presenta una relación positiva fuerte con `views`, lo que indica que los videos más vistos suelen recibir más interacciones positivas.
- La regresión lineal funciona como una primera aproximación, aunque el comportamiento de las visualizaciones también depende de otros factores no presentes en el dataset.

## Licencia de uso

Este proyecto se publica con fines académicos bajo la licencia **MIT**. El dataset original pertenece a sus respectivos autores y se utiliza únicamente con fines educativos.
