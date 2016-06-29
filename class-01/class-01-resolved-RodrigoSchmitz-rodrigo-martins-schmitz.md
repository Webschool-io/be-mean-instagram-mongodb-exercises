# MongoDB - Aula 01 - Exercício
autor: Rodrigo Martins Schmitz

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-02T01:17:19.528-0200    connected to: localhost
2016-01-02T01:17:19.530-0200    dropping: be-mean.restaurantes
2016-01-02T01:17:21.097-0200    imported 25359 documents

```

## Contando os restaurantes


```
db.restaurantes.find({}).count()
25359

```