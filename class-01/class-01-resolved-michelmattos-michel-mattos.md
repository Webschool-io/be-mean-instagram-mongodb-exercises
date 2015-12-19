# MongoDB - Aula 01 - Exercício
autor: Michel Mattos

## Importando os restaurantes

```
$ mongoimport --db be-mean-instagram -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-15T12:37:14.696-0200 dropping: be-mean-instagram.restaurantes
2015-11-15T12:37:16.169-0200 check 9 25359
2015-11-15T12:37:16.169-0200 imported 25359 objects
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```