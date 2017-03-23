# MongoDB - Aula 01 - Exercício
autor: Edison Ferraz

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2017-02-24T23:46:14.725-0300    connected to: localhost
2017-02-24T23:46:14.764-0300    dropping: be-mean.restaurantes
2017-02-24T23:46:16.362-0300    imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```