# MongoDB - Aula 01 - Exercício
autor: Higor Diego

## Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file rest.json
2015-11-10T16:04:38.818-0200    connected to: localhost
2015-11-10T16:04:38.819-0200    dropping: be-mean.restaurantes
2015-11-10T16:04:40.488-0200    imported 25359 documents


## Contando os restaurantes
> db.restaurantes.find({}).count()
25359



