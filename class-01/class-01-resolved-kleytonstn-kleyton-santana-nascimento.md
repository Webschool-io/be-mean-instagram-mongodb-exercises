# MongoDB - Aula 01 - Exercício
autor: Kleyton Santana Nascimento

## Importando os restaurantes

mongoimport --db mongo-db --collection restaurantes --drop restaurantes.json 
2017-02-19T11:12:20.730-0300	connected to: localhost
2017-02-19T11:12:20.731-0300	dropping: mongo-db.restaurantes
2017-02-19T11:12:23.492-0300	imported 25359 documents

## Contando os restaurantes

> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
