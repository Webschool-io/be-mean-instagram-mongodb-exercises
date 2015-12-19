# MongoDB - Aula 01 - Exercício
autor: Victor Igor

## Importando os restaurantes
	```
	mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	2015-11-19T02:29:46.049-0400	connected to: 127.0.0.1
	2015-11-19T02:29:46.062-0400	dropping: be-mean.restaurantes
	2015-11-19T02:29:47.991-0400	imported 25359 documents

	```
## Contando os restaurantes
	```

	db.restaurantes.find({}).count()
	25359

	```
