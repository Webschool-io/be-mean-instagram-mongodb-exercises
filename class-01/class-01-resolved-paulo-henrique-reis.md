# MongoDB - Aula 01 - Exercício
Autor: Paulo Henrique Reis

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2017-06-18T13:44:24.649-0300    connected to: 127.0.0.1
2017-06-18T13:44:24.660-0300    dropping: be-mean.restaurantes
2017-06-18T13:44:27.440-0300    imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

```