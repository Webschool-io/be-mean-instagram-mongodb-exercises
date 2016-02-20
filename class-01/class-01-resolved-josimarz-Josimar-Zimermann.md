# MongoDB - Aula 01 - Exercício
autor: Josimar Zimermann

## Importando os restaurantes

	```
	mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
	2016-02-20T12:01:14.982-0200	connected to: localhost
	2016-02-20T12:01:14.983-0200	dropping: be-mean.restaurantes
	2016-02-20T12:01:15.719-0200	imported 25359 documents
	
	```

## Contando os restaurantes

	```
	nightwolf(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
	25359

	```