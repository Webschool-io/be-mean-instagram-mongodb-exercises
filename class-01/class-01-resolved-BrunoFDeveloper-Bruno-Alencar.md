
# MongoDB - Aula 01 - Exercício
autor: Bruno Alencar

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-09T21:47:20.229-0200	connected to: localhost
2016-02-09T21:47:20.230-0200	dropping: be-mean.restaurantes
2016-02-09T21:47:21.053-0200	imported 25359 documents

```

## Selecionando o banco de dados

```
MacBook-Pro-de-bruno(mongod-3.2.0) be-mean> use be-mean
switched to db be-mean

```

## Contando os restaurantes

```
MacBook-Pro-de-bruno(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
25359

```