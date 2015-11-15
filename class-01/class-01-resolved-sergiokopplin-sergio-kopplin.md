# MongoDB - Aula 01 - Exercício
autor: Sérgio Kopplin

## Importando a collection

```
mongoimport --db be-mean --collection restaurantes --drop --file Desktop/restaurantes.json
2015-11-12T18:56:03.368-0200	connected to: localhost
2015-11-12T18:56:03.369-0200	dropping: be-mean.restaurantes
2015-11-12T18:56:04.570-0200	imported 25359 documents
```

## Contando os registros

```
Sergios-MacBook-Pro(mongod-3.0.7) test> use be-mean;
switched to db be-mean
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
```
