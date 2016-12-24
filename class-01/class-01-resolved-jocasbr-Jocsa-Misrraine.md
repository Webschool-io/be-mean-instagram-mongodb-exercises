# MongoDB - Aula 01 - Exercício
autor: Jocsã Misrraine

## Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file aula01_restaurantes.json
2016-08-09T21:36:03.209-0300	connected to: localhost
2016-08-09T21:36:03.210-0300	dropping: be-mean.restaurantes
2016-08-09T21:36:05.561-0300	imported 25359 documents

## Contando os restaurantes
(mongod-3.2.8) be-mean> db.restaurantes.find().count()
25359

