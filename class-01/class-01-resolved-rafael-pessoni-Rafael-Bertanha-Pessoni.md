#MongoDB - Aula 01 - Exercício

	```	
	Autor: Rafael Pessoni

	```

##Importando os restaurantes

	```
	mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	2016-01-03T15:30:03.032-0300	connected to: 127.0.0.1
	2016-01-03T15:30:03.032-0300	dropping: be-mean.restaurantes
	2016-01-03T15:30:04.280-0300	imported 25359 documents

	```

##Selecionando o banco de dados

	```
	localhost(mongod-3.2.0) test> use be-mean
	switched to db be-mean

	```

##Contando os restaurantes

	```
	localhost(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
	25359

	```
