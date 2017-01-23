#MongoDb - Aula01 - Exercício
autor: André Affonso

##Importando os restaurantes



>mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2017-01-23T15:44:05.723-0200    connected to: 127.0.0.1
2017-01-23T15:44:05.750-0200    dropping: be-mean.restaurantes
2017-01-23T15:44:07.511-0200    imported 25359 documents


##Contando os restaurantes

> db.restaurantes.find({}).count()
25359