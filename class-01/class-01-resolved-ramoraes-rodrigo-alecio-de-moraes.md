 # MongoDB - Aula 01 - Exercício
autor: Rodrigo Alécio de Moraes

## Importando os restaurantes

```
$ mongoimport --db be-mean -c restaurantes --file "C:\Users\rodrigoalecio\Desktop\Rodrigo\Material_consulta\WebMean\dados.json"
2016-05-18T12:54:52.764-0300    connected to: localhost
2016-05-18T12:54:54.395-0300    imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

```