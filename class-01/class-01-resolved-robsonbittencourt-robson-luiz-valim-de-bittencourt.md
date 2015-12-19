# MongoDB - Aula 01 - Exercício
autor: Robson Luiz Valim de Bittencourt

## Importando os restaurantes

```

mongoimport --db be-mean --collection restaurantes --drop --file /home/robson/Desktop/restaurantes.json
2015-11-15T13:51:37.769-0200	connected to: localhost
2015-11-15T13:51:37.770-0200	dropping: be-mean.restaurantes
2015-11-15T13:51:39.125-0200	imported 25359 documents

```

## Contando os restaurantes

```

db.restaurantes.find({}).count()
25359


```