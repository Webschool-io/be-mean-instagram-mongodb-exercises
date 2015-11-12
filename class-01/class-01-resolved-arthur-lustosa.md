MongoDB - Aula 01 - Exercício

Autor: Arthur Lustosa

Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes 
2015-11-12T14:33:02.103-0300	connected to: localhost
2015-11-12T14:33:02.104-0300	dropping: be-mean.restaurantes
2015-11-12T14:33:03.320-0300	imported 25359 documents


Contando os restaurantes

arthur@souza-pc:~$ mongo
MongoDB shell version: 3.0.7
connecting to: test
> show dbs
be-mean  0.078GB
local    0.078GB
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359

