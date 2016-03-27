# MongoDB - Aula 01 - Exercício
autor: Adilton Valaszek

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-10T13:09:36.047-0200    connected to: localhost
2016-02-10T13:09:36.047-0200    dropping: be-mean.restaurantes
2016-02-10T13:09:39.014-0200    [##############..........] be-mean.restaurantes7.0 MB/11.4 MB (61.6%)
2016-02-10T13:09:40.004-0200    imported 25359 documents
```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359

```