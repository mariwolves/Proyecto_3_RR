# Proyecto_3_RR 📓💵
En este proyecto, se llevará a cabo un análisis de riesgo relativo y una validación de hipótesis utilizando una base de datos bancaria. Para ello, utilizaremos dos herramientas destacadas en el ámbito del análisis de datos: BigQuery y Looker Studio.



# Índice 
- [Introducción](#introducción)
- [Equipo 🤝](#equipo)
- [Herramientas :hammer_and_pick:](#herramientas)
- [Lenguajes](#lenguajes)
- [Procesamiento y análisis](#procesamiento-y-análisis)
  - [Procesamiento de los datos](#procesamiento-de-los-datos)
  - [Análisis exploratorio](#análisis-exploratorio)
  - [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)
- [Enlaces](#enlaces)
  
## Introducción
En el sector bancario, es crucial contar con la seguridad y certeza necesarias para tomar decisiones informadas y estratégicas. Para ello, se emplean diversas técnicas de análisis que permiten obtener una visión clara y fundamentada. Una de estas herramientas es el análisis del riesgo relativo, que nos proporciona un marco para evaluar probabilidades y tomar decisiones basadas en datos. Este análisis nos permitirá validar o refutar tres hipótesis clave.

En el desarrollo de estas hipótesis, se utilizarán dos poderosas herramientas de análisis de datos: BigQuery y Looker Studio, junto con una base de datos proporcionada por el banco "Super Caja". Estas herramientas facilitarán la comprensión y evaluación de los patrones de riesgo, permitiendo un enfoque basado en datos para la toma de decisiones financieras.


Hipótesis:
+ :one: “Los jóvenes tienen un mayor riesgo de impago”.
+ 2️⃣ “Las personas con más cantidad de préstamos activos tienen mayor riesgos de ser malos pagadores”.
+ 3️⃣ “Las personas que han retrasado sus pagos por más de 90 días tienen mayor riesgo de ser malos pagadores”.

Objetivos:
+ 🔷 El propósito de este proyecto es verificar estas hipótesis a través del análisis de datos y ofrecer recomendaciones estratégicas fundamentadas en los resultados obtenidos, con la meta de mejorar las probabilidades de éxito del nuevo artista.
  +  🔹Desarrollar un marco de análisis.
		    +  Establecer un método sistemático para analizar hitos financieros.
  +  🔹
  +  🔹
## Equipo 
- [María José L](https://github.com/mariwolves)


## Herramientas
+ BigQuery  
+ Power BI
  
## Lenguajes
+ SQL
## Procesamiento y análisis
Este proceso se dividió en tres etapas, en cada una de las cuales se aplicaron técnicas y programas específicos de acuerdo con los objetivos planteados.
##  Procesamiento de los datos 
El tratamiento de los datos se realizó en BigQuery utilizando comandos SQL. Los pasos seguidos fueron los siguientes:
+ Identificar valores nulos a través COUNTIF e IS NULL.
+ Manejar datos nulos con COALESCE
+ Identificar duplicados a través de COUNT, GROUP BY, HAVING.
+ Manejar variables que no son útiles en el análisis a través de EXCEPT.
+ Identificar datos discrepantes en variables categóricas con REGEXP_REPLACE.
+ Identificar datos discrepantes con datos que superan el rango de los enteros de 32 bits con INT64.
+ Identificar datos discrepantes en variables numéricas con MAX, MIN y AVG.
+ Comprobar y modificar tipos de datos con SAFE_CAST y CAST.
+ Crear nuevas variables utilizando CONCAT, SUM y DATE.
+ Descartar filas con NOT IN
+ Construir tablas auxiliares utilizando WITH.
+ Unir las tablas utilizando LEFT JOIN.

## Análisis exploratorio
+ Agrupar datos según variables categóricas a través de tablas
+ Visualizar las variables categóricas a través de gráficos de barras y líneas 
+ Aplicar medidas de tendencia central y dispersión (avg, median, max, min, standard deviation) en BPM, Playlists en spotify, Charts en spotify, Charts en Apple/Deezer/Shazam Playliststotal y Streams
+ Visualizar distribución a través de Hitogramas BPM, Playlist en spotify, Playliststotal y Streams

## Validación de hipótesis
La validación de hipótesis se realizó en BigQuery, y los resultados se visualizaron en gráficos mediante Power BI
+ Análisis de correlación entre métricas (Coeficiente de Pearson)

## Resultados
### Validación de hipótesis
  + **Hipótesis 1**: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
    + **Conclusión**: :x: No existe relación entre ambas variables, prácticamente no hay relación entre las pulsaciones por minuto de una canción y su cantidad de reproducciones.
      + *Coeficiente de Pearson* (-0.002336...) Correlación negativa extremadamente débil. 
![image]

  + **Hipótesis 2**: Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
    + **Conclusión**: :heavy_check_mark: Indica una relación lineal positiva moderada entre estas dos variables, lo que sugiere una considerable similitud en las preferencias de los usuarios de ambas plataformas.
      + *Coeficiente de Pearson* (0.59998...) 
![image]

  + **Hipótesis 3**: La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
    + **Conclusión**: :heavy_check_mark: Indica una relación lineal positiva fuerte entre estas dos variables, lo que sugiere que las canciones que están en más playlists tienden a recibir más streams.
      + *Coeficiente de Pearson* (0.78356...)
![image]
  + **Hipótesis 4**: Los artistas con un mayor número de canciones en Spotify tienen más streams.
    + **Conclusión**: :heavy_check_mark: Existe una relación directa entre la cantidad de canciones que un artista tiene en Spotify y la cantidad de streams que recibe. Cuanto mayor sea el catálogo de un artista en la plataforma, mayor será la probabilidad de que acumule un mayor número de streams.
      + *Coeficiente de Pearson* (0.8907...)
![image]

  + **Hipótesis 5**: Las características de la canción influyen en el éxito en términos de streams en Spotify
    + **Conclusión**: :x: Las características no influyen en el número de streams que obtiene una canción, según los resultados obtenidos (-0,...). Esto sugiere una falta de correlación lineal entre estas características y el número de streams.
      + *Coeficiente de Pearson*
      +  danceability -0.105
      +  valence -0.041
      +  energy -0.025
      +  acousticness -0.005
      +  instrumentalness -0.044
      +  liveness -0.049
      +  speechiness -0.112
![image]

## Conclusiones
"El éxito de una canción o artista se basa en los siguientes aspectos:
+ **Estrategias de Distribución y Marketing:** La popularidad de una canción, medida en términos de streams, está influenciada por estrategias de distribución y marketing, tales como su inclusión en listas de reproducción destacadas, su posición en rankings y su presencia en diversas plataformas.
  ![image]

+ **Volumen de Contenido:** La cantidad total de canciones de un artista está estrechamente vinculada a su éxito en términos de streams, indicando que una mayor producción de contenido puede atraer una mayor cantidad de reproducciones."
  ![image]

## Recomendaciones
Con base en las conclusiones, se recomienda:
+ **Presencia en Plataformas:** Asegúrate de estar disponible en diversas plataformas de streaming, tales como Spotify, Tidal, Apple Music, Amazon Music, Qobuz, Deezer y YouTube Music.
+ **Diversidad de Contenido:** Considera ofrecer una variedad de canciones para atraer a diferentes tipos de oyentes.



## Enlaces
### [Presentación] 
### [Dashboard] 
### [Video Loom] 
