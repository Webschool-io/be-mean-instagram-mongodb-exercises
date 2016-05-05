# MongoDB - Aula 01 - Exercício
autor: André Rocha

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-12T22:15:04.065-0200	connected to: localhost
2015-11-12T22:15:04.066-0200	dropping: be-mean.restaurantes
2015-11-12T22:15:05.947-0200	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```