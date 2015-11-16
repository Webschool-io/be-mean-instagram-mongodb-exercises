# MongoDB - Aula 01 - Exercício
autor: Pedro Henrique Prado Oliveira

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --host=127.0.0.1 --drop --file restaurantes.json
2015-11-16T10:22:26.930-0200    connected to: 127.0.0.1
2015-11-16T10:22:26.934-0200    dropping: be-mean.restaurantes
2015-11-16T10:22:28.614-0200    imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
