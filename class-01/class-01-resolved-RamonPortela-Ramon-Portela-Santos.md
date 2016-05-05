# MongoDB - Aula 01 - Exercício
autor: Ramon Portela Santos

## Importando os restaurantes

```
? mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-21T20:54:11.356-0200    connected to: localhost
2015-11-21T20:54:11.357-0200    dropping: be-mean.restaurantes
2015-11-21T20:54:12.254-0200    imported 25359 documents
```

## Contando os restaurantes
```
Ramon-PC(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
```