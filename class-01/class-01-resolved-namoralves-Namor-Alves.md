# MongoDB - Aula 01 - Exercício

Autor: Namor Alves

## Importando os restaurantes

``` shell
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-09T14:15:50.073-0300    connected to: localhost
2016-02-09T14:15:50.074-0300    dropping: be-mean.restaurantes
2016-02-09T14:15:51.379-0300    imported 25359 documents
```

## Contando os restaurantes

```
Namor-PC(mongod-3.2.1) test> use be-mean
switched to db be-mean
Namor-PC(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359
Namor-PC(mongod-3.2.1) be-mean>
```
