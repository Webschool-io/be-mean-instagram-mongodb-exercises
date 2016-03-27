# MongoDB - Aula 01 - Exercício
autor: Fagner Silva

## Importando os restaurantes

```
mongoimport --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json
2016-03-05T23:52:17.918-0300	connected to: localhost
2016-03-05T23:52:17.930-0300	dropping: be-mean-instagram.collection
2016-03-05T23:52:20.911-0300	[##########..............] be-mean-instagram.collection	5.2 MB/11.4 MB (45.5%)
2016-03-05T23:52:23.915-0300	[#####################...] be-mean-instagram.collection	10.1 MB/11.4 MB (88.5%)
2016-03-05T23:52:24.810-0300	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```