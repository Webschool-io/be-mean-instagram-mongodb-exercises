# MongoDB - Aula 01 - Exercício
autor: Alexandre D'Agostin

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file desktop/restaurantes.json
2015-11-09T22:32:41.884-0200	connected to: localhost
2015-11-09T22:32:41.885-0200	dropping: be-mean.restaurantes
2015-11-09T22:32:43.753-0200	imported 25359 documents

```

## Contando os restaurantes

```
aledagostin(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

```