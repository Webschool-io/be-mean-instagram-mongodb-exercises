# MongoDB - Aula 01 - Exercício

Autor: Vinicius Reis

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-20T23:44:07.074-0200	connected to: localhost
2015-11-20T23:44:07.074-0200	dropping: be-mean.restaurantes
2015-11-20T23:44:07.840-0200	imported 25359 documents
```

## Contando os restaurantes

```
use be-mean
switched to db be-mean
db.restaurantes.find({}).count()
25359
```
