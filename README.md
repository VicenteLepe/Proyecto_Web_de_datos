# Proyecto_Web_de_datos

## Ejecutar generación de triples

´´

~$ cd tarql/target/appassembler


~$ sh bin/tarql --ntriples ../../../games-ttl-generator.sparql ../../../games-data-clean.csv > ../../../games-data-triples.ttl


~$ sort -u ../../../games-data-triples.ttl -o ../../../games-data-triples.ttl

´´
## Herramientas y dataset

https://tarql.github.io

https://jena.apache.org/documentation/fuseki2

https://www.kaggle.com/datasets/brunovr/metacritic-videogames-data


