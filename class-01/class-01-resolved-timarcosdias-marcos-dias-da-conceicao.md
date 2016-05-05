# MongoDB - Aula 01 - Exercício
Autor: Marcos Dias da Conceição

## Importando os restaurantes
```
root@marcos-pc:/# mongoimport --db be-mean --collection restaurantes --drop --file /DATA/Documents/GitHub/be-mean/restaurantes.json
connected to: 127.0.0.1
2015-12-26T02:42:26.539-0300 dropping: be-mean.restaurantes
2015-12-26T02:42:26.969-0300 check 9 25359
2015-12-26T02:42:27.042-0300 imported 25359 objects
```
## Contando os restaurantes
```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```
