# MongoDB - Aula 01 - Exercício
autor: Vagner Pereira Silva

## Importando os restaurantes

H:\mongodb\bin>mongoimport --db be-mean --collection restaurantes --drop --file
F:\CursoMongoDB\restaurantes.json
2015-12-21T23:12:30.551-0200    connected to: localhost
2015-12-21T23:12:30.555-0200    dropping: be-mean.restaurantes
2015-12-21T23:12:32.214-0200    imported 25359 documents


## Contando os restaurantes

H:\mongodb\bin>mongo be-mean
MongoDB shell version: 3.2.0
connecting to: be-mean
> db.restaurantes.find().count()
25359
>




