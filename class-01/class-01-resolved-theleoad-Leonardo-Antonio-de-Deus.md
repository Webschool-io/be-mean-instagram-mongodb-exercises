# MongoDB - Aula 01 - Exercício
Autor: Leonardo Antonio de Deus

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file /Users/theleoad/downloads/restaurantes.json
2015-12-28T21:31:37.733-0200	connected to: localhost
2015-12-28T21:31:37.733-0200	dropping: be-mean.restaurantes
2015-12-28T21:31:40.717-0200	[##########..............] be-mean.restaurantes	5.2 MB/11.4 MB (45.5%)
2015-12-28T21:31:43.169-0200	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
2015-12-28T21:31:43.169-0200	imported 25359 documents
```

## Contando os restaurantes

```
Leonardos-MBP(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
25359
```
