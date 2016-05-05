# MongoDB - Aula 01 - Exercício
autor : João Antonio Gardin Vieira

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
2016-02-09T02:19:22.285-0200	connected to: localhost
2016-02-09T02:19:22.285-0200	dropping: be-mean.restaurantes
2016-02-09T02:19:23.383-0200	imported 25359 documents
```

## Contando os restaurantes

```
mongo
MongoDB shell version: 3.2.1
connecting to: test
> db.restaurantes.find({}).count()
0
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```
