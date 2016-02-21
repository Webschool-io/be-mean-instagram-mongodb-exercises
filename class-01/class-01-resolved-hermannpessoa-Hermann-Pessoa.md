# MongoDB - Aula 01 - Exercício
autor: HERMANN PESSOA

## Importando os restaurantes

```
environment:be-mean-instagram-mongodb performaweb$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-21T15:57:05.580-0300	connected to: localhost
2016-02-21T15:57:05.582-0300	dropping: be-mean.restaurantes
2016-02-21T15:57:07.874-0300	imported 25359 documents

```

## Contando os restaurantes

```
environment(mongod-3.0.7) test> use be-mean
switched to db be-mean
environment(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

```


