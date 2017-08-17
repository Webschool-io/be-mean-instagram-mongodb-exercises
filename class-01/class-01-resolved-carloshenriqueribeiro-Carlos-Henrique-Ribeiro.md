# MongoDB - Aula 01 - Exercício

Autor: Carlos Henrique Ribeiro

## Importando os restaurantes

``` shell
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2017-08-17T10:13:24.679-0300    connected to: localhost
2017-08-17T10:13:24.680-0300    dropping: be-mean.restaurantes
2017-08-17T10:13:25.954-0300    imported 25359 documents
```

## Contando os restaurantes

```
> show dbs
> use be-mean
> db.restaurantes.find({}).count()
25359
```
