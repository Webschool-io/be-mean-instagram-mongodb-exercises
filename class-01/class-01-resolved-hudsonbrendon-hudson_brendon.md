
# MongoDB - Aula 01 - Exercício
autor: Hudson Brendon

## Importando os restaurantes
	hudsonbrendon@ubuntu:~/Github/be-mean$ mongoimport --db be-mean --collection restaurants --drop --file restaurantes.json
	connected to: 127.0.0.1
	Tue Nov 17 22:51:49.882 dropping: be-mean.restaurants
	Tue Nov 17 22:51:52.023 		Progress: 7352464/11906303	61%
	Tue Nov 17 22:51:52.023 			13600	4533/second
	Tue Nov 17 22:51:53.695 check 9 25359
	Tue Nov 17 22:51:55.485 imported 25359 objects


## Contando os restaurantes
	hudsonbrendon@ubuntu:~$ mongo
	MongoDB shell version: 2.4.9
	connecting to: test
	Mongo-Hacker 0.0.8
	ubuntu(mongod-2.4.9) test> use be-mean
	switched to db be-mean
	ubuntu(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
	25359
