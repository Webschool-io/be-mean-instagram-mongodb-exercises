# MongoDB - Aula 01 - Exercício
autor: Kalyane Lordao

## Importando os restaurantes



mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-07-29T19:38:48.034-0300	connected to: localhost
2016-07-29T19:38:48.035-0300	dropping: be-mean.restaurantes
2016-07-29T19:38:49.169-0300	imported 25359 documents



## Contando os restaurantes 


db.restaurantes.find({}).count()
25359
