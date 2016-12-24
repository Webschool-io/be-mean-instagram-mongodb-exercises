# MongoDB - Aula 01 - Exercício
autor: Maicon Giovani Lopes da Cunha Ferreira

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-05-12T10:38:21.163-0300	connected to: localhost
2016-05-12T10:38:21.253-0300	dropping: be-mean.restaurantes
2016-05-12T10:38:23.782-0300	imported 25359 documents
```

## Contando os restaurantes

```
doom(mongod-3.2.0) be-mean-instagram> db.restaurantes.find({}).count()
25359
```

