# MongoDB - Aula 01 - Exercício
Autor: Juliano Padilha

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-07-03T00:29:30.154-0300	connected to: 127.0.0.1
2016-07-03T00:29:30.154-0300	dropping: be-mean.restaurantes
2016-07-03T00:29:32.139-0300	imported 25359 documents
```

## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```