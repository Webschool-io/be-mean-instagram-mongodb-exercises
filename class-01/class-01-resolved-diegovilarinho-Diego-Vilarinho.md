# MongoDB - Aula 01 - Exercício
autor: Diego Vilarinho

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file mongoimpots/restaurantes.json 
2016-04-10T15:48:33.131-0300    connected to: localhost
2016-04-10T15:48:33.132-0300    dropping: be-mean.restaurantes
2016-04-10T15:48:34.699-0300    imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

```