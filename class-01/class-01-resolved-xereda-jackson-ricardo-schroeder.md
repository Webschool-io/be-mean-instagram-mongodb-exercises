# MongoDB - Aula 01 - Exercício
autor: Jackson Ricardo Schroeder

## Importando os restaurantes

```
xereda$ mongoimport --db be-mean --collection restaurantes --file restaurantes.json --drop
2016-05-16T21:53:12.318-0300	connected to: localhost
2016-05-16T21:53:12.319-0300	dropping: be-mean.restaurantes
2016-05-16T21:53:14.798-0300	imported 25359 documents
```

## Contando os restaurantes

```
mongo
MongoDB shell version: 3.2.0
connecting to: test
Mongo-Hacker 0.0.13
macminixereda(mongod-3.2.0)> use be-mean
switched to db be-mean
macminixereda(mongod-3.2.0) be-mean> db.restaurantes.find({}).count();
25359
```
