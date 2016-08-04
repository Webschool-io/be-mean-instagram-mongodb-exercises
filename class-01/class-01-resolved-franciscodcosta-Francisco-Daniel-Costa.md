# MongoDB - Aula 01 - Exercício
autor: Francisco Daniel Costa

## Importando os restaurantes

```
franciscodcosta@insta-mongodb:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-07-20T22:54:31.746+0000    connected to: localhost
2016-07-20T22:54:31.754+0000    dropping: be-mean.restaurantes
2016-07-20T22:54:33.287+0000    imported 25359 documents
```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359
```
