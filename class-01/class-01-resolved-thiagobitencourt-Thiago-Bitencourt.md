# MongoDB - Aula 01 - Exercício
autor: Thiago R. M. Bitencourt

## Importando os restaurantes

	mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2016-07-03T21:01:35.536-0300	connected to: localhost
	2016-07-03T21:01:35.536-0300	dropping: be-mean.restaurantes
	2016-07-03T21:01:38.342-0300	imported 25359 documents

## Contando os restaurantes

	db.restaurantes.find({}).count()
	25359
