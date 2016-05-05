# MongoDB - Aula 01 - Exercício
autor: Ivan Diniz

## Importando os restaurantes

```
2015-12-19T19:30:51.702-0300	connected to: localhost
2015-12-19T19:30:51.735-0300	dropping: be-mean.restaurantes
2015-12-19T19:30:54.348-0300	[####################....] be-mean.restaurantes	9.8 MB/11.4 MB (86.2%)
2015-12-19T19:30:54.662-0300	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
2015-12-19T19:30:54.662-0300	imported 25359 documents
```

## Contando os restaurantes

```
MBP-de-Ivan(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
25359
```