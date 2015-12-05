# MongoDB - Aula 01 - Exercício
autor: André Luiz de França Bazoli

## Importando os restaurantes
mongoimport --db be-mean --collection restaurantes --drop --file C:\restaurantes.json
2015-11-17T12:24:40.475-0200    connected to: localhost
2015-11-17T12:24:40.476-0200    dropping: be-mean.restaurantes
2015-11-17T12:24:41.584-0200    imported 25359 documents


## Contando os restaurantes
C:\>mongo
MongoDB shell version: 3.0.4
connecting to: test
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
