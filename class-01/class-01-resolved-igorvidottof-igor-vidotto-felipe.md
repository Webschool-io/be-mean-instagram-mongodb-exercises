# MongoDB - Aula 01 - Exercício
autor: Igor Vidotto Felipe

## Importando os restaurantes
```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-15T13:34:59.651-0200	connected to: localhost
2015-11-15T13:34:59.651-0200	dropping: be-mean.restaurantes
2015-11-15T13:35:01.402-0200	imported 25359 documents
```

## Contando os restaurantes
```
igorpc(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
```
