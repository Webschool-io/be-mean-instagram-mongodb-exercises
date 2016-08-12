# MongoDB - Aula 01 - Exercício
autor: Sadraque Santos

## Importando os restaurantes

```
quasar:~ Quasar$ mongoimport --db be-mean --collection restaurantes --drop --file data.json
2016-07-17T14:15:13.710-0300	connected to: localhost
2016-07-17T14:15:13.710-0300	dropping: be-mean.restaurantes
2016-07-17T14:15:15.176-0300	imported 25359 documents
```

## Contando os restaurantes

```
quasar(mongod-3.2.7) be-mean> db.restaurantes.find({}).count()
25359
```
