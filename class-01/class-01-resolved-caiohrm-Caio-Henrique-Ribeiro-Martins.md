# MongoDB - Aula 01 - Exercício
autor: Caio Henrique Ribeiro Martins

## Importando os restaurantes

caio@caio-pc:~$ mongoimport --db be-mean --collection restaurantes --drop --file /home/caio/Downloads/restaurantes.json 
2016-06-07T14:24:44.169-0300	connected to: localhost
2016-06-07T14:24:44.171-0300	dropping: be-mean.restaurantes
2016-06-07T14:24:47.091-0300	[#######################.] be-mean.restaurantes11.0 MB/11.4 MB (97.0%)
2016-06-07T14:24:47.295-0300	[########################] be-mean.restaurantes11.4 MB/11.4 MB (100.0%)
2016-06-07T14:24:47.295-0300	imported 25359 documents


## Contando os restaurantes

> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count();
25359

