# MongoDB - Aula 01 - Exercício
autor: Márcio Dias

## Importando collection
```
marcio-mac:class-01 marciodias$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-16T15:33:47.754-0200	connected to: localhost
2015-11-16T15:33:47.755-0200	dropping: be-mean.restaurantes
2015-11-16T15:33:49.981-0200	imported 25359 documents

```

## Count restaurantes

```
> db.restaurantes.find({}).count()
25359