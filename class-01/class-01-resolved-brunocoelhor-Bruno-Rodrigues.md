# MongoDB - Aula 01 - Exercício
autor: Bruno Coelho Rodrigues

## Importando os restaurantes

> mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-11-15T16:31:55.057-0200	connected to: 127.0.0.1
2015-11-15T16:31:55.057-0200	dropping: be-mean.restaurantes
2015-11-15T16:31:56.016-0200	imported 25359 documents

## Contando os restaurantes

>bruno-dev(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
