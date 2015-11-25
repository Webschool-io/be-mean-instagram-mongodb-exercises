# MongoDB - Aula 01 - Exercício
autor: Marco Antonio Ribeiro (https://github.com/marcoribeirojr)

## Importando os restaurantes

mongoimport --db be-mean-instagram --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-24T10:15:49.412-0200 dropping: be-mean-instagram.restaurantes
2015-11-24T10:15:50.706-0200 check 9 25359
2015-11-24T10:15:50.735-0200 imported 25359 objects

## Contando os restaurantes

db.restaurantes.find({}).count()
  
25359
