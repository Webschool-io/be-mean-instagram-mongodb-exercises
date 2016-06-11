# MongoDB - Aula 01 - Exercício
autor: Daury

## Importando os restaurantes

Daury@DAURY-PC MINGW64 ~/Desktop/BeMEAN/1. BeMEAN - MongoDB/be-mean-instagram-mo                                                                                                                ngodb-excercises
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json                                                                                                            2016-05-25T12:10:22.869-0300    connected to: localhost
2016-05-25T12:10:22.876-0300    dropping: be-mean.restaurantes
2016-05-25T12:10:25.843-0300    [#################.......] be-mean.restaurantes 8.5 MB/11.4 MB (74.9%)
2016-05-25T12:10:27.573-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-05-25T12:10:27.573-0300    imported 25359 documents

## Contando os restaurantes

Daury@DAURY-PC MINGW64 ~/Desktop/BeMEAN/1. BeMEAN - MongoDB/be-mean-instagram-mo                                                                                                                ngodb-excercises
$ mongo
MongoDB shell version: 3.2.6
connecting to: test
db
test
use be-mean
switched to db be-mean
db.restaurantes.find({}).count()
25359

