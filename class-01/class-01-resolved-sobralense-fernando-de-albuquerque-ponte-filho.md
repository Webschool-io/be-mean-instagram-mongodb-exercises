# MongoDB - Aula 01 - Exercício
autor: Fernando de Albuquerque Ponte Filho

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json                                             
2015-11-17T02:13:37.765-0300	connected to: 127.0.0.1
2015-11-17T02:13:37.766-0300	dropping: be-mean.restaurantes
2015-11-17T02:13:40.765-0300	[####################....] be-mean.restaurantes	9.8 MB/11.4 MB (86.2%)
2015-11-17T02:13:41.437-0300	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
2015-11-17T02:13:41.437-0300	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count();
25359
```
