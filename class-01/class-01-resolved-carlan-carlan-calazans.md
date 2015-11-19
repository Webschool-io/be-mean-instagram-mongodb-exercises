# MongoDB - Aula 01 - Exercício
autor: Carlan Calazans

## Importanto os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-17T15:59:14.163+0000    connected to: localhost
2015-11-17T15:59:14.165+0000    dropping: be-mean.restaurantes
2015-11-17T15:59:17.132+0000    [####################....] be-mean.restaurantes9.8 MB/11.4 MB (86.2%)
2015-11-17T15:59:17.826+0000    imported 25359 documents
```

## Contando os restaurantes

```
mongo be-mean
MongoDB shell version: 3.0.7
connecting to: be-mean
Mongo-Hacker 0.0.8
bemeaninstagram(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
```