# MongoDB - Aula 01 - Exercício
autor: Felipe Marques da Silva

## Importando os restaurantes

2016-02-16T12:16:56.899-0300	connected to: localhost
2016-02-16T12:16:56.899-0300	dropping: be-mean.restaurantes
clear2016-02-16T12:16:59.778-0300	[####################....] be-mean.restaurantes	9.8 MB/11.4 MB (86.3%)
2016-02-16T12:17:00.275-0300	[########################] be-mean.restaurantes11.4 MB/11.4 MB (100.0%)
2016-02-16T12:17:00.275-0300	imported 25359 documents

## Selecionando o Banco Be-Mean

MacBook-Pro-de-Felpe(mongod-3.2.1) test> use be-mean
switched to db be-mean


## Contando os restaurantes

MacBook-Pro-de-Felpe(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359
