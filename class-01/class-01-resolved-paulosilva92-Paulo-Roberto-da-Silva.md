# MongoDB - Aula 01 - Exercício
autor: Paulo Roberto da Silva

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file rest
aurantes.json
2016-02-05T22:03:13.061-0200    connected to: 127.0.0.1
2016-02-05T22:03:13.074-0200    dropping: be-mean.restaurantes
2016-02-05T22:03:14.437-0200    imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
