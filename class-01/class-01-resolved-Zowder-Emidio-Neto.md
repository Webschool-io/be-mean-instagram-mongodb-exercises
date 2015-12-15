# MongoDB - Aula 01 - Exercício
autor: Emídio de Paiva Neto

## Importando os restaurantes

wasdev@ubuntu:~$ mongoimport --db be-mean --collection restaurantes --drop --file Workspace/exercicios-modulo-mongodb/restaurantes.json
2015-12-05T10:09:41.218-0800	connected to: localhost
2015-12-05T10:09:41.231-0800	dropping: be-mean.restaurantes
2015-12-05T10:09:43.859-0800	imported 25359 documents

## Contando os restaurantes

ubuntu(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359


