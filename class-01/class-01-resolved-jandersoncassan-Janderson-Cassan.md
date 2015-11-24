# MongoDB - Aula 01 - Exercício
autor: Janderson Cassan 

## Importando os restaurantes

C:\Program Files\MongoDB\Server\3.0\bin>mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-09T21:31:22.005-0200	connected to: localhost
2015-11-09T21:31:22.006-0200	dropping: be-mean.restaurantes
2015-11-09T21:31:22.704-0200	imported 25359 documents

## Contando os restaurantes

      db.restaurantes.find({}).count()
	25359
	>
