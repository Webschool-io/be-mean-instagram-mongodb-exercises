# MongoDB - Aula 01 - Exercício
autor: Diêgo Bolina

## Importando os restaurantes
➜  be-mean-mine git:(master) ✗ mongoimport --db be-mean-sky  --collection restaurantes --drop --file restaurantes.json;
2015-12-14T18:52:45.011-0200    connected to: localhost
2015-12-14T18:52:45.012-0200    dropping: be-mean-sky.restaurantes
2015-12-14T18:52:45.990-0200    imported 25359 documents

## Contando os restaurantes

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-sky> db.restaurantes.find({}).count()
25359