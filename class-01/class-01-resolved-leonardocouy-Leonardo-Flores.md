# MongoDB - Aula 01 - Exercício
autor: Leonardo Flores

## Importando os restaurantes

```
mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json;
2016-03-15T11:13:26.797-0300	connected to: localhost
2016-03-15T11:13:26.798-0300	dropping: be-mean.restaurantes
2016-03-15T11:13:27.517-0300	imported 25359 documents
```

## Contando os restaurantes

```
MBP-de-Leonardo(mongod-3.2.1) be-mean> db.restaurantes.find({}).count()
25359

```
