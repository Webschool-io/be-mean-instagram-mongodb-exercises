# MongoDB - Aula 01 - Exercício
autor: Luiz Paulo Rodrigues

## Importando os restaurantes

C:\Users\ELIAS\Documents\Paulinho\estudos\be-mean-instagram\Apostila\module-mongodb\data
λ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-06T19:58:55.007-0200    connected to: localhost
2015-12-06T19:58:55.011-0200    dropping: be-mean.restaurantes
2015-12-06T19:58:56.617-0200    imported 25359 documents

## Contando os restaurantes

C:\Users\ELIAS\Documents\Paulinho\estudos\be-mean-instagram\Apostila\module-mongodb\data
> db.restaurantes.find({}).count()
25359