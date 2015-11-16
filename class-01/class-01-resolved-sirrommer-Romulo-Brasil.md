# MongoDB - Aula 01 - Exercício
autor: Rômulo Brasil 

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file /Users/romulobrasil/Desktop/restaurantes.json
2015-11-09T20:33:50.473-0300	connected to: localhost
2015-11-09T20:33:50.474-0300	dropping: be-mean.restaurantes
2015-11-09T20:33:53.461-0300	[####################....] be-mean.restaurantes9.8 MB/11.3 MB (86.3%)
2015-11-09T20:33:53.741-0300	imported 25359 documents

```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359

```