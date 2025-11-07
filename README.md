# Proyecto_Web_de_datos


~$ cd tarql/target/appassembler


~$ sh bin/tarql --ntriples ../../../games-data-clean.sparql ../../../games-data-clean2.csv > games-data-triples.ttl


~$ sort -u ../../../games-data-triples.ttl -o ../../../games-data-triples.ttl


# Definir tripletas dentro de games-data.sparql

```
PREFIX ex: <http://ex.org/a#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

CONSTRUCT {
  ?URI a ex:Organization;
    ex:permalink ?permalink;
    ex:name ?company;
    ex:employees ?numEmployees;
    ex:category ?category;
    ex:city ?city;
    ex:state ?state;
    ex:fundationDate ?fundedDate;
    ex:raisedAmt ?amount;
    ex:raisedCurrency ?raisedCurrency;
    ex:round ?round;
} 
FROM <file:TechCrunchcontinentalUSA.csv> 
WHERE {
  BIND (URI(CONCAT('http://ex.org/companies/', ?permalink)) AS ?URI)
  BIND (xsd:integer(?numEmps) AS ?numEmployees)
  BIND (xsd:decimal(?raisedAmt) AS ?amount)
}
```