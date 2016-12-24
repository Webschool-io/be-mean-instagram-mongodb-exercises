# MongoDB - Aula 01 - Exercício
autor: Samuel Pacheco

## Importando os restaurantes


	mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	connected to: 127.0.0.1
	2016-08-16T02:02:15.064-0300 dropping: be-mean.restaurantes
	2016-08-16T02:02:15.854-0300 check 9 25359
	2016-08-16T02:02:16.082-0300 imported 25359 objects


## Contando os restaurantes
	

	> db.restaurantes.find({}).count()
	25359

