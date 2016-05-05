MongoDB - Aula 01 - Exercício
Autor: Nicolas de Paulo Rosa

Importando os restaurantes

nicolas@MEAN:~/Downloads$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-12T21:25:24.630-0200	connected to: localhost
2015-11-12T21:25:24.631-0200	dropping: be-mean.restaurantes
2015-11-12T21:25:26.160-0200	imported 25359 documents

Contando os restaurantes

MEAN(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

