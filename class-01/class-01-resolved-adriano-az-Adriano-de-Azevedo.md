# MongoDB - Aula 01 - Exercício
autor: Adriano de Azevedo

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2017-04-25T10:17:00.717-0400    connected to: 127.0.0.1
2017-04-25T10:17:00.719-0400    dropping: be-mean.restaurantes
2017-04-25T10:17:02.228-0400    imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
