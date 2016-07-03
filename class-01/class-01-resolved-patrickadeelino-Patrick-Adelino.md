# MongoDB - Aula 01 - Exercício

Autor: Patrick Adelino

## Importando os restaurantes

```
mongoimport -db be-mean -collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
Sun Jul  3 13:04:31.405 dropping: be-mean.restaurantes
Sun Jul  3 13:04:34.179 		Progress: 4755932/11906303	39%
Sun Jul  3 13:04:34.182 			8800	2933/second
Sun Jul  3 13:04:35.484 check 9 25359
Sun Jul  3 13:04:37.561 imported 25359 objects

```

## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> show collections
restaurantes
system.indexes
> db.restaurantes.find({}).count()
25359

```
