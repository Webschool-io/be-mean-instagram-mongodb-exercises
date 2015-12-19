# MongoDB - Aula 01 - Exercício
autor: RONEI CHIARANDI

## Importando os restaurantes

```
mongoimport -d be-mean -c restaurantes --drop --file ex-01/restaurantes.json
connected to: 127.0.0.1
2015-11-09T20:12:00.407-0200 dropping: be-mean.restaurantes
2015-11-09T20:12:02.028-0200 check 9 25359
2015-11-09T20:12:02.097-0200 imported 25359 objects

```

## Contando os restaurantes

```
hOMeR(mongod-2.6.7) be-mean> db.restaurantes.find({}).count()
25359

```
