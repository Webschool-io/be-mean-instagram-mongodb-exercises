# MongoDB - Aula 01 - Exercício
autor: Deivid da Gama Cardoso

## Importando os restaurantes
ozodrac@OZODRAC-PC2 /c/users/ozodrac/documents/github/be-mean-instagram/apostila/classes/mongodb (master)

$ mongoimport --db be-mean --collection restaurantes --drop --file
restaurantes.json
2015-11-21T00:59:10.822-0200    connected to: localhost
2015-11-21T00:59:10.840-0200    dropping: be-mean.restaurantes
2015-11-21T00:59:12.468-0200    imported 25359 documents


## Contando os restaurantes
PS C:\WINDOWS\system32> mongo
MongoDB shell version: 3.0.7
connecting to: test
Server has startup warnings:
2015-11-21T00:52:29.074-0200 I CONTROL  [initandlisten] ** NOTE: This is a 32-bit MongoDB binary running on a 64-bit operating
2015-11-21T00:52:29.075-0200 I CONTROL  [initandlisten] **      system. Switch to a 64-bit build of MongoDB to
2015-11-21T00:52:29.075-0200 I CONTROL  [initandlisten] **      support larger databases.
2015-11-21T00:52:29.076-0200 I CONTROL  [initandlisten]
2015-11-21T00:52:29.077-0200 I CONTROL  [initandlisten]
2015-11-21T00:52:29.078-0200 I CONTROL  [initandlisten] ** NOTE: This is a 32 bit MongoDB binary.
2015-11-21T00:52:29.079-0200 I CONTROL  [initandlisten] **       32 bit builds are limited to less than 2GB of data (or less with --journal).
2015-11-21T00:52:29.080-0200 I CONTROL  [initandlisten] **       See http://dochub.mongodb.org/core/32bit
2015-11-21T00:52:29.081-0200 I CONTROL  [initandlisten]
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
