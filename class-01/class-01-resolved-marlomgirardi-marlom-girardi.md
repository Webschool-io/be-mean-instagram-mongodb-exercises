# MongoDB - Aula 01 - Exercício
autor: Marlom Girardi

## Importando os restaurantes

```
marlom@trusty:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-20T14:48:51.054-0200	connected to: localhost
2015-12-20T14:48:51.054-0200	dropping: be-mean.restaurantes
2015-12-20T14:48:52.618-0200	imported 25359 documents
```

## Contando os restaurantes

```
trusty(mongod-3.0.8) be-mean> db.restaurantes.find({}).count()
25359
```
