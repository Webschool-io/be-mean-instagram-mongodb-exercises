# MongoDB - Aula 01 - Exercício
autor: Guilherme Henrique Escarabel Silva

## Importando os restaurantes

```
	Guilherme-PC:aula-01-mongo-db guilhermeescarabel$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2016-03-31T20:20:42.692-0400	connected to: localhost
	2016-03-31T20:20:42.692-0400	dropping: be-mean.restaurantes
	2016-03-31T20:20:45.597-0400	imported 25359 documents
```


## Contando os restaurantes

```
	Guilherme-PC(mongod-3.2.4) be-mean> db.restaurantes.find({}).count();
	25359	
```	
 