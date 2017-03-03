# MongoDB - Aula 01 - Exercício
autor: Bruno Motta Azevedo do Nascimento

## Importando os restaurantes

```
MacBook-Pro:aula-01 Bruno$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-10-18T02:02:57.783-0200	connected to: localhost
2016-10-18T02:02:57.783-0200	dropping: be-mean.restaurantes
2016-10-18T02:02:58.592-0200	imported 25359 documents

```

## Contando os restaurantes

```
MacBook-Pro:aula-01 Bruno$ mongo
MongoDB shell version: 3.2.10
connecting to: test
Mongo-Hacker 0.0.14
Server has startup warnings:
2016-10-18T01:19:35.547-0200 I CONTROL  [initandlisten]
2016-10-18T01:19:35.547-0200 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
MacBook-Pro(mongod-3.2.10) test> use be-mean
switched to db be-mean
MacBook-Pro(mongod-3.2.10) be-mean> db.restaurantes.find({}).count()
25359

```