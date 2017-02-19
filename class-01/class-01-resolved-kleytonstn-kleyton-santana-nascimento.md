# MongoDB - Aula 01 - Exercício
autor: Kleyton Santana Nascimento

## Importando os restaurantes

kleytonstn@ghost:~/Documents/MongoDB$ mongoimport --db mongo-db --collection restaurantes --drop restaurantes.json 
2017-02-19T11:12:20.730-0300	connected to: localhost
2017-02-19T11:12:20.731-0300	dropping: mongo-db.restaurantes
2017-02-19T11:12:23.492-0300	imported 25359 documents

## Contando os restaurantes

MongoDB shell version v3.4.2
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.4.2

> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359

