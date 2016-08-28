# MongoDB - Aula 01 - Exercício
Author: Leonardo Fragas

## Importando os dados

```
fbitt@LEONARDO-PC C:\nodeprojects\be-mean-instagram-mongodb\exercises
$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-08-27T11:54:23.694-0300    connected to: 127.0.0.1
2016-08-27T11:54:23.709-0300    dropping: be-mean.restaurantes
2016-08-27T11:54:25.710-0300    imported 25359 documents
```

## Fazendo count dos dados

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```