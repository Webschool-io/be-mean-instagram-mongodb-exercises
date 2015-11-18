# MongoDB - Aula 01 - Exercício
autor: Diego Bittencourt Silva

## Importando os restaurantes
diego@DESKTOP-B86UP9T MINGW64 ~/desktop/Curso Instagram BE-MEAN/Be-Mean/Mongodb/Aula1
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json.txt
2015-11-16T17:23:02.192-0200    connected to: localhost
2015-11-16T17:23:02.194-0200    dropping: be-mean.restaurantes
2015-11-16T17:23:03.593-0200    imported 25359 documents


## Contando os restaurantes
diego@DESKTOP-B86UP9T MINGW64 ~/desktop/Curso Instagram BE-MEAN/Be-Mean/Mongodb/Aula1
$ mongo
MongoDB shell version: 3.0.7
connecting to: test
use be-mean
switched to db be-mean
db.restaurantes.find({}).count();
25359
