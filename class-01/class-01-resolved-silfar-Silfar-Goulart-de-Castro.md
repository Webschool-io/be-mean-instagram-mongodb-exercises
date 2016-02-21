# MongoDB - Aula 01 - Exercício
autor: Silfar Goulart de Castro

## Importando os restaurantes
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-02-18T22:59:36.811-0200    connected to: 127.0.0.1
2016-02-18T22:59:36.813-0200    dropping: be-mean.restaurantes
2016-02-18T22:59:38.342-0200    imported 25359 documents

C:\Users\Silfar\Downloads>mongo
MongoDB shell version: 3.2.3
connecting to: test
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359