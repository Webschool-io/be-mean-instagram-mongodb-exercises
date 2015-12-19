# MongoDB - Aula 01 - Exercício
autor: Fabio Rodrigo Magalhães

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-11-16T11:37:49.999-0200    connected to: 127.0.0.1
2015-11-16T11:37:50.001-0200    dropping: be-mean.restaurantes
2015-11-16T11:37:50.149-0200    imported 25359 documents	
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```