# MongoDB - Aula 01 - Exercício
autor: Julio Rodrigues

## Importando os restaurantes

MBP-de-Julio:exercicios juliorodrigues$ mongoimport --db be-mean --collection restaurantes --drop restaurantes.json
2016-07-14T19:42:47.812-0300	connected to: localhost
2016-07-14T19:42:47.813-0300	dropping: be-mean.restaurantes
2016-07-14T19:42:50.803-0300	[############............] be-mean.restaurantes	5.7 MB/11.3 MB (50.0%)
2016-07-14T19:42:51.957-0300	[########################] be-mean.restaurantes	11.3 MB/11.3 MB (100.0%)
2016-07-14T19:42:51.957-0300	imported 25359 documents
MBP-de-Julio:exercicios juliorodrigues$ 


## Contando os restaurantes

> db.restaurantes.find({}).count()
25359
> 
