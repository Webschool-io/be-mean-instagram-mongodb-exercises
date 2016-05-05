# MongoDB - Aula 01 - Exercício
autor: Leonardo Colodette

## Importando os restaurantes

```
	mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	connected to: 127.0.0.1
	2016-01-05T09:55:56.897-0200 dropping: be-mean.restaurantes
	2016-01-05T09:55:58.558-0200 check 9 25359
	2016-01-05T09:56:00.083-0200 imported 25359 objects
```

## Contando os restaurantes

```
    db.restaurantes.find({}).count()
    25359

```
