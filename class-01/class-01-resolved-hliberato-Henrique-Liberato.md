MongoDB - Aula 01 - Exercício
autor: Henrique Liberato

## Importando os restaurantes

henrique@henrique:~$ mongoimport --db be-mean --collection restaurantes --drop --file /home/henrique/be_mean/data/restaurantes.json
2016-03-01T11:42:53.022-0300	connected to: localhost
2016-03-01T11:42:53.023-0300	dropping: be-mean.restaurantes
2016-03-01T11:42:54.894-0300	imported 25359 documents

## Contando os restaurantes

> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()