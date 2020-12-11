
# Pipelines Project: Analizando el dataset de Top Running Times.


- 1.Encontrar el dataset.

En primer lugar, seleccionamos un dataset sobre el que realizar nuestra investigación. Hemos seleccionado Top Running Times por ser un tema de interés personal, de mi agrado y en el que podría desarrollar y añadir ideas puesto que conozco la temática.

- 2.Estudio y limpieza del dataset.

Una vez seleccionado, nos disponemos a estudiarlo, seleccionar la información que queremos, lo limpiamos y lo preparamos para nuestro análisis de datos. Este dataset contiene el ranking de tiempos de diferentes categorias tales como 100m, 200m, 400m, 10.000m, maratones... Es un dataset muy amplio, muy bien organizado y limpio (perfecto para trabajar sobre él), por lo que nos centramos en la categoria de 100metros para filtrar bastante su contenido y poder estudiarlo con detalle.

Durante el proceso de data cleaning, primero observamos y eliminamos las filas con valores nulos, posteriormente filtramos la columna "Event" con los tiempos de las carreras de 100 metros solamente.

En este proceso de limpieza, nos dimos cuenta que los valores exactos tales como 10 segundos, o 11 segundos, no contenían sus decimales, por lo que decidimos añadirlos para que todos los datos de la tabla siguieran el mismo patrón.

Finalmente, añadimos dos columnas nuevas a la tabla. La primera (km/h), muestra la velocidad media que tuvo ese corredor en la carrera de 100m. La añadimos mediante una lambda. La siguiente columna (que fue añadida un poco más adelante) muestra el año en el que tuvo lugar la carrera. Es una columna muy similar a la fecha de la carrera, pero solo queremos centrarnos en el año ya que pensamos que sería buena idea averiguar en ese top 50 de mejores tiempos, agrupar dentro de cada año el número de veces que se habian logrado buenos tiempos.

- 3.API

Una vez terminado el data cleaning, decidimos averiguar la temperatura que hizo en la ciudad donde se disputaron las carreras. Pensamos que sería interesante comparar las diferentes temperaturas y ver si había algun dato interesante que pudiera influir, que ayudara a lograr mejores tiempos o averiguar la temperatura ideal para batir récords de tiempos.

Por restricciones de la API, tuvimos que reducir a 50 las filas a procesar. Otro problema que nos encontramos fue que cuando sacamos las temperaturas, algunas ciudades nos dieron valores nulos ya que no existia registro de esa ciudad(ciudades como Eugene o Athínai. Quizas por ser demasiado pequeñas y no estar registradas en la web del tiempo).

Iteramos sobre la tabla "df" mediante la formula "irerrows()". Asi le pedimos que busque la ciudad, la fecha, y pase esos valores como argumentos a la formula "temperature" que hemos creado y con la que llamaremos a la web del tiempo para que nos devuelva la temperatura en esa ciudad, en ese dia. Ese dato que nos devuelve, ademas, lo incluiremos en una lista "temps" que añadiremos como una columna más al final de la tabla.

- 4.Analisis y Conclusiones.

Una vez tenemos las tablas con la información que queremos, procedemos a crear tablas que muestren ciertos resultados.

Primero hemos mostrado la velocidad media máxima, mínima, la media y su desviación estandar. Puesto que son resultados muy ajustados, la diferencia entre ellos es muy pequeña, como era de esperar. La desviación tipica es menor de 2 decimas. Todo esto es razonable teniendo en cuenta que el mejor tiempo de los 100 metros es de 09.58seg y el top 50 es de 09.81seg.

Tambien hemos mostrado otras tablas tales como el listado de corredores que ocupan las 50 mejores marcas. Aqui observamos como algunos de ellos aparecen varias veces en esta lista (como es el caso de Usain Bolt que aparece 15 veces en este ranking, poca broma).

Otra gráfica que nos pareció curiosa mostrar fue el listado de paises de procedencia de estos atletas. Curiosamente el top 50 de mejores tiempos lo copan tan solo dos paises en todo el mundo. Estos son Jamaica y USA con el 60% y el 40% de apariciones en el ranking, respectivamente.

Una de las ultimas gráficas que mostramos fue la grafica de temperaturas. En ella agrupamos las 50 carreras en función de la temperatura que hacia ese dia en esa ciudad concreta. Curiosamente con temperaturas entre 17 y 23 grados se han batido 23 de esos 50 mejores tiempos, por lo que podriamos afirmar que la temperatura ideal para hacer buenos tiempos en carreras de 100m seria de entre 17 y 23 grados, siendo 23 grados la temperatura con la que más veces se han hecho muy buenos tiempos.

Por último mostramos la grafica con la cantidad de mejores tiempos conseguidos cada año. Aqui observamos que los mejores tiempos se han dado con más frecuencia en los ultimos años, concretamente entre 2008 y 2015, y podriamos decir que las mejoras tecnologicas y los estudios/avances médicos en el mundo del deporte podrían haber influido a conseguir tantas buenas marcas en la ultima decada aproximadamente (sin menospreciar en absoluto las habilidades de corredores de la talla de Usain Bolt, Tison Gay o Asafa Powell, entre otros). Creo que en los ultimos 10/15 años se ha explorado mucho más a fondo cómo mejorar el rendimiento de los atletas profesionales (en cualquier disciplina deportiva), se ha estudiado como influyen factores tales como la alimentación, el descanso, la comida, etc. Todos estos conocimientos, unidos a las mejoras técnologicas (material deportivo que ayuda al deportista a rendir mejor, materiales más ligeros, productos que se hacen a medida del propio atleta, etc) se han podido sumar tambien a las habilidades innatas del corredor para potenciar su rendimiento.