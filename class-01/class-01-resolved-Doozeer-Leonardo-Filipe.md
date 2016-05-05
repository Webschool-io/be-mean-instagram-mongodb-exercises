# MongoDB - Aula 01 - Exercício
autor: LEONARDO FILIPE

## Importando os restaurantes

```
mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
2015-12-15T16:05:17.633-0200	connected to: localhost
2015-12-15T16:05:17.634-0200	dropping: be-mean.restaurantes
2015-12-15T16:05:18.310-0200	imported 25359 documents

```

## Contando os restaurantes

```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
25359

```