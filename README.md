# Proyecto_Web_de_datos


~$ cd tarql/target/appassembler


~$ sh bin/tarql --ntriples ../../../games-data-clean.sparql ../../../games-data-clean2.csv > games-data-triples.ttl


~$ sort -u ../../../games-data-triples.ttl -o ../../../games-data-triples.ttl


# Definir tripletas dentro de games-data.sparql

```
PREFIX ex: <http://example.org/game#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

CONSTRUCT {
  ?gameURI a ex:Game ;
       ex:name ?name ;
       ex:platform ?platform ;
       ex:releaseDate ?releaseDate ;
       ex:score ?scoreValue ;
       ex:userScore ?userScoreValue ;
       ex:developer ?developer ;
       ex:genre ?genre ;
       ex:players ?players ;
       ex:critics ?criticsNum ;
       ex:users ?usersNum .
}
FROM <file:games-data-clean.csv>
WHERE {
  BIND(URI(CONCAT(CONCAT("http://ex.org/games/",ENCODE_FOR_URI(REPLACE(STR(?name), "[^A-Za-z0-9]+", "_")),ENCODE_FOR_URI(REPLACE(STR(?platform), "[^A-Za-z0-9]+", "_"))))) AS ?gameURI)
  BIND(xsd:date(?r_date) AS ?releaseDate)
  BIND(xsd:integer(?score) AS ?scoreValue)
  BIND(xsd:decimal(?user_score) AS ?userScoreValue)
  BIND(xsd:integer(?critics) AS ?criticsNum)
  BIND(xsd:integer(?users) AS ?usersNum)
}
```