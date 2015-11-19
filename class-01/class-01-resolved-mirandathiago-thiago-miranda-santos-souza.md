# MongoDB - Aula 01 - Exercício
autor: THIAGO MIRANDA DOS SANTOS SOUZA

## Importando os restaurantes

$ mongoimport --db be-mean --collection restaurantes --drop --file "restaurantes.json"
2015-11-18T21:38:18.492-0300    connected to: localhost
2015-11-18T21:38:18.495-0300    dropping: be-mean.restaurantes
2015-11-18T21:38:21.480-0300    [####################....] be-mean.restaurantes9.8 MB/11.4 MB (86.2%)
2015-11-18T21:38:22.264-0300    imported 25359 documents

## Contando os restaurantes
$ mongo be-mean
MongoDB shell version: 3.0.7
connecting to: be-mean
db.restaurantes.find({}).count()
25359
