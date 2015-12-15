# MongoDB - Aula 01 - Exercício
autor: OTAVIO PIRES

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-12-02T14:00:47.472+0000    connected to: 127.0.0.1
2015-12-02T14:00:47.475+0000    dropping: be-mean.restaurantes
2015-12-02T14:00:50.475+0000    [################........] be-mean.restaurantes 7.7 MB/11.4 MB (67.7%)
2015-12-02T14:00:52.200+0000    imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

```