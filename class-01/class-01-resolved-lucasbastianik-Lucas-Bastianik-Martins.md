# MongoDB - Aula 01 - Exercício
autor: Lucas Bastianik Martins

## Importando os restaurantes
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-24T23:44:20.132-0200	connected to: localhost
2015-11-24T23:44:20.133-0200	dropping: be-mean.restaurantes
2015-11-24T23:44:21.410-0200	imported 25359 documents

## Contando os restaurantes
mbp-lucasbastianik(mongod-3.0.7) be-mean> db.restaurantes.find().count()
25359