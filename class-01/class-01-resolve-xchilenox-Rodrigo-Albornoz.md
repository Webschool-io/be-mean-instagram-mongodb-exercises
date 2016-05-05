# MongoDB - Aula 01 - Exercício

Autor: Rodrigo Albornoz

## Importando os restaurantes

``` shell
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-28T14:46:01.148-0200	connected to: localhost
2016-01-28T14:46:01.148-0200	dropping: be-mean.restaurantes
2016-01-28T14:46:03.148-0200    imported 25359 documents
```

## Contando os restaurantes

```
ubuntu-vm(mongod-3.0.9) test> use be-mean
switched to db be-mean
ubuntu-vm(mongod-3.0.9) be-mean> db.restaurantes.find({}).count()
25359
```
