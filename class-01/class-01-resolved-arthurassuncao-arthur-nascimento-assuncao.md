# MongoDB - Aula 01 - Exercício
autor: Arthur Nascimento Assuncao

## Importando os restaurantes
```
arthur@assuncao ~/cursos/be-mean/be-mean-instagram-mongodb-excercises $ mongoimport --db be-mean --collection restaurantes --drop --file ../mongodb_files/aula01/restaurantes.json
2015-11-17T22:15:05.039-0200	connected to: localhost
2015-11-17T22:15:05.040-0200	dropping: be-mean.restaurantes
2015-11-17T22:15:07.696-0200	imported 25359 documents
```

## Contando os restaurantes
```
arthur@assuncao ~/cursos/be-mean/be-mean-instagram-mongodb-excercises $ mongo
MongoDB shell version: 3.0.7
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
> 
```