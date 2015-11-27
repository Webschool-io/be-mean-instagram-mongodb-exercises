# MongoDB - Aula01 - Exercício
autor: Douglas Salin Zuqueto

## Importando os restaurantes

```
[dzuqueto@fedora WebSchool]$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-24T02:20:42.304-0200	connected to: localhost
2015-11-24T02:20:42.304-0200	dropping: be-mean.restaurantes
2015-11-24T02:20:43.308-0200	imported 25359 documents

```

## Contando os restaurantes
```
fedora(mongod-3.0.4) test> use be-mean
switched to db be-mean
fedora(mongod-3.0.4) be-mean> db.restaurantes.find().count()
25359

```
