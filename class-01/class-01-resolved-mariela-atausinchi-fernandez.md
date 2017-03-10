# MongoDb - Aula 01 - Exercicio
autor: Mariela Atausinchi Fernandez

## Importando os restaurantes

	```
	mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	connected to: 127.0.0.1
	2017-03-09T16:32:13.590-0300 dropping: be-mean.restaurantes
	2017-03-09T16:32:14.206-0300 check 9 25359
	2017-03-09T16:32:14.226-0300 imported 25359 objects
	```


## Contando os restaurantes

	```
	cem-008046106(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
	25359
	```

