# MongoDB - Aula 01 - Exercício
autor: Everton Ferreira Dos Santos 

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-11-17T23:38:35.837-0200    connected to: 127.0.0.1
2016-11-17T23:38:35.841-0200    dropping: be-mean.restaurantes
2016-11-17T23:38:38.738-0200    [####################....] be-mean.restaurantes 9.6 MB/11.4 MB (84.8%)
2016-11-17T23:38:40.010-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-11-17T23:38:40.011-0200    imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
