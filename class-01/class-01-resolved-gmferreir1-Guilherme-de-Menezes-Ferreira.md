# MongoDB - Aula 01 - Exercício
autor: Guilherme de Menezes Ferreira

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-10T15:16:09.946-0200	connected to: localhost
2016-02-10T15:16:09.947-0200	dropping: be-mean.restaurantes
2016-02-10T15:16:11.316-0200	imported 25359 documents
```

## Contando os restaurantes

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) test> use be-mean
switched to db be-mean
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean> 
```
