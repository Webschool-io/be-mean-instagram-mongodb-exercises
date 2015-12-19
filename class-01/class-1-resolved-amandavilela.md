# MongoDB - Aula 01 - Exercício
autor: Amanda Vilela

## Importando os restaurantes

```
mongoimport --db be-mean -collection restaurantes --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 21 11:09:44.977 check 9 25359
Sat Nov 21 11:09:45.211 imported 25359 objects

```

## Contando os restaurantes

```
amanda-Inspiron-7520(mongod-2.4.9) test> use be-mean
switched to db be-mean
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359

```
