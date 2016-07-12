# MongoDB - Aula 01 - Exercício

autor: David Araujo

## Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json

2016-04-02T21:28:10.516-0300	connected to: localhost
2016-04-02T21:28:10.516-0300	dropping: be-mean.restaurantes
2016-04-02T21:28:11.776-0300	imported 25359 documents

## Contando os restaurantes

> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
>
