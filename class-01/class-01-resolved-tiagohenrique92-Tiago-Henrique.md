# MongDB - Aula 01 - Exercício
autor: Tiago Henrique

## Importando os restaurantes

```
t2@t2-lubuntu:~/projetos/be-mean/mongo-db/files$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
2015-11-15T22:59:09.992-0200	connected to: localhost
2015-11-15T22:59:09.994-0200	dropping: be-mean.restaurantes
2015-11-15T22:59:12.988-0200	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
2015-11-15T22:59:13.007-0200	imported 25359 documents

```

## Contando os restaurantes

```
t2-lubuntu(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359

```
