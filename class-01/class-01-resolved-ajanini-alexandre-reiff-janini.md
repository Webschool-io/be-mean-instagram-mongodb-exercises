# MongoDB - Aula 01 - Exercício
autor: Alexandre Reiff Janini

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-13T09:23:20.033-0200    connected to: localhost
2015-11-13T09:23:20.034-0200    dropping: be-mean.restaurantes
2015-11-13T09:23:21.200-0200    imported 25359 documents
```

## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```