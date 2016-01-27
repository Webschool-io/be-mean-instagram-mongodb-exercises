# MongoDB - Aula 01 - Exercício
autor: Maurício Júnior

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurants.json
2016-01-26T22:55:23.047-0200    connected to: 127.0.0.1
2016-01-26T22:55:23.069-0200    dropping: be-mean.restaurantes
2016-01-26T22:55:25.152-0200    imported 25359 documents
```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359
```