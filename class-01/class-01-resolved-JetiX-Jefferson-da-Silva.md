# MongoDB - Aula 01 - Exercício
autor: Jefferson da Silva

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-08T04:59:44.343-0300	connected to: localhost
2016-02-08T04:59:44.344-0300	dropping: be-mean.restaurantes
2016-02-08T04:59:45.412-0300	imported 25359 documents

```

## Contando os restaurantes

```
jefferson(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359
```
