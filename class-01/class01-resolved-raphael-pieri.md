#MongoDB - Aula01 - Exercicio
autor: Raphael De Pieri

##Importando os restaurantes

mongoimport -db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-17T01:55:00.555-0200 dropping: be-mean.restaurantes
2015-11-17T01:55:01.354-0200 check 9 25359
2015-11-17T01:55:01.423-0200 imported 25359 objects

##Contando os restaurantes

db.restaurantes.find({}).count()
25359



