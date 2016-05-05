# MongoDB - Aula 01 - Exercício
autor: FABIO

## Importando os restaurantes

```
> mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-02T22:24:20.177-0200    connected to: localhost
2015-12-02T22:24:20.178-0200    dropping: be-mean.restaurantes
2015-12-02T22:24:22.114-0200    imported 25359 documents
```

## Contando os restaurantes

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) test> use be-mean
switched to db be-mean
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean> db.restaurantes.find({}).count()
25359
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean>

```