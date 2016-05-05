# MongoDB - Aula 01 - Exercício
Autor: Rafael Moreira Pinho Pradella

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-29T02:55:50.365-0200    connected to: localhost
2015-12-29T02:55:50.366-0200    dropping: be-mean.restaurantes
2015-12-29T02:55:53.333-0200    [###############.........] be-mean.restaurantes7.3 MB/11.4 MB (64.5%)
2015-12-29T02:55:54.853-0200    [########################] be-mean.restaurantes11.4 MB/11.4 MB (100.0%)
2015-12-29T02:55:54.853-0200    imported 25359 documents

```

## Contando os restaurantes

```
Mac-mini-de-Rafael-Pradella(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
25359

```