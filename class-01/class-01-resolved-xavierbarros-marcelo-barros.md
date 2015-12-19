# MongoDB - Aula 01 - Exercício

autor: Marcelo Barros

## Importando os restaurantes

exercicios git:(master) mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-11-13T12:02:49.055-0200	connected to: 127.0.0.1
2015-11-13T12:02:49.055-0200	dropping: be-mean.restaurantes
2015-11-13T12:02:49.953-0200	imported 25359 documents

## Contando os restaurantes

maba(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359