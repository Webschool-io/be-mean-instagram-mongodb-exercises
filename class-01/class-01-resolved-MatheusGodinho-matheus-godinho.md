# MongoDB - Aula 01 - Exercício

Autor: Matheus Godinho

## Importando os restaurantes

``` shell
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
2016-02-07T16:18:30.970-0200	connected to: 127.0.0.1
2016-02-07T16:18:30.971-0200	dropping: be-mean.restaurantes
2016-02-07T16:18:31.894-0200	imported 25359 documents
```

## Contando os restaurantes

```
MACBEPIDUCB174(mongod-3.2.1) test> use be-mean
switched to db be-mean
MACBEPIDUCB174(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359
```