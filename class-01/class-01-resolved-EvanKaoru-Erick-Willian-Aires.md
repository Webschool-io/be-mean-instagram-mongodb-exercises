#MONGODB - AULA 01 - Exercício
Autor: Erick Willian Aires

## Importando os Restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --file ../restaurantes.json
connected to: 127.0.0.1
Sat Jan 23 18:04:51.317 dropping: be-mean.restaurantes
Sat Jan 23 18:04:54.571                 Progress: 7015063/11906303      58%
Sat Jan 23 18:04:54.571                         13000   4333/second
Sat Jan 23 18:04:56.340 check 9 25359
Sat Jan 23 18:04:56.341 imported 25359 objects
```

## Contando Restaurantes
```
$ mongo be-mean
MongoDB shell version: 2.4.9
connecting to: be-mean
> db.restaurantes.find({}).count()
25359
>
```
