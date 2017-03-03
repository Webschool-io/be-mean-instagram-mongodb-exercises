# MongoDB - Aula 01 - Exercício
autor: Ronaldo Feitosa

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
connected to: 127.0.0.1
2016-03-12T16:07:36.987-0300 dropping: be-mean.restaurantes
2016-03-12T16:07:38.070-0300 check 9 25359
2016-03-12T16:07:38.178-0300 imported 25359 objects

```

## Contando os restaurantes

```
ronaldo-ubuntu(mongod-2.6.10) test> use be-mean
switched to db be-mean
ronaldo-ubuntu(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
25359

```