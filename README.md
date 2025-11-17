# Proyecto_Web_de_datos

## Ejecución del proyecto

Primero se extrae el dataset desde https://www.kaggle.com/datasets/brunovr/metacritic-videogames-data, se ejecuta el jupyter Proyecto Web de Datos.ipynb que lee este dataset en csv, en particular, el último bloque  que limpia los datos (cambiando el formato de la fecha, y eliminando valores no númericos de columnas numéricas).

Luego, con Tarql y un archivo generador games-ttl-generator.sparql se realiza la conversión del dataset resultante games-data-clean.csv, ejecutando los siguientes comandos:

```
~$ cd tarql/target/appassembler


~$ sh bin/tarql --ntriples ../../../games-ttl-generator.sparql ../../../games-data-clean.csv > ../../../games-data-triples.ttl


~$ sort -u ../../../games-data-triples.ttl -o ../../../games-data-triples.ttl

```

Destacar que aunque Tarql está incluido en el repositorio, es altamente recomendable instalarlo de forma independiente.

Finalmente, se sube el archivo de triples RDF resultante games-data-triples.ttl al servidor Apache Jena Fuseki para elaborar las consultas, estas consultas están contenidas en consultasfinales.sparql
## Herramientas y dataset

- https://tarql.github.io

- https://jena.apache.org/documentation/fuseki2

- https://www.kaggle.com/datasets/brunovr/metacritic-videogames-data


