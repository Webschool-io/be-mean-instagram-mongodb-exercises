# MongoDB - Aula 01 - Exercício

Autor: Deyves Carvalho

## Importando os restaurantes

``` shell
mongoimport -db be-mean --collection restaurantes --drop --file /var/www/html/bemeanInstagram/mongodb/exercicios/restaurantes.json   
connected to: 127.0.0.1
Fri Mar 11 00:27:58.644 dropping: be-mean.restaurantes
Fri Mar 11 00:27:59.399 check 9 25359
Fri Mar 11 00:27:59.443 imported 25359 objects
```

## Contando os restaurantes

```
deyves-dev-NE56R(mongod-2.4.9) test> use be-mean
switched to db be-mean
deyves-dev-NE56R(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```
