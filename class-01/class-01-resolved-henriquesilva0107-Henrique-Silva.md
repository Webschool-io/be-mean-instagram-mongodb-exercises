# MongoDB - Aula 01 - Exercício
autor: Henrique Silva

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-11-23T01:37:07.325-0200	connected to: 127.0.0.1
2016-11-23T01:37:07.325-0200	dropping: be-mean.restaurantes
2016-11-23T01:37:08.304-0200	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
