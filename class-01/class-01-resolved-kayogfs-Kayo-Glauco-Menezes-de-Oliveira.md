# MongoDB - Aula 01 - Exercicio
autor: Kayo Glauco

## Importando os restaurantes

	kayo@Sparta:~/be-MEAN/Mongo/aula 01$ mongoimport --db be-mean -c restaurantes --drop --file restaurantes.json
	connected to: 127.0.0.1
	2016-03-20T13:53:32.483-0300 dropping: be-mean.restaurantes
	2016-03-20T13:53:33.623-0300 check 9 25359
	2016-03-20T13:53:33.661-0300 imported 25359 objects

## Contando os restaurantes

	kayo@Sparta:~/be-MEAN/Mongo/aula 01$ mongo
	MongoDB shell version: 2.6.10
	connecting to: test
	Mongo-Hacker 0.0.13
	Sparta(mongod-2.6.10) test> use be-mean
	switched to db be-mean
	Sparta(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
	25359


