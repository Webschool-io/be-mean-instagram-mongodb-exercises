# MongoDB - Aula 01 - Exercício
autor: Cristiano Mesquita

## Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2016-05-27T23:24:53.402-0300 dropping: be-mean.restaurantes
2016-05-27T23:24:54.590-0300 check 9 25359
2016-05-27T23:24:54.590-0300 imported 25359 objects

## Contando os restaurantes

db.restaurantes.find({}).count()
25359

