# MongoDB - Aula 01 - Exercício
autor: William Bewzenko de Jesus

## Importando os restaurantes

```
mongoimport --db be-mean  --collection restaurantes --drop --file ../restaurantes.json 
2016-01-04T13:30:49.549-0200	connected to: localhost
2016-01-04T13:30:49.550-0200	dropping: be-mean.restaurantes
2016-01-04T13:30:50.631-0200	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find().count()
25359
```
