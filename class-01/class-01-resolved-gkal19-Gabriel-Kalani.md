#MONGODB - AULA 01 - Exercício
Author: Gabriel Kalani

##Importação dos restaurantes

```
gkal19:~/workspace $ mongoimport --db db --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2016-01-27T16:55:28.456+0000 dropping: db.restaurantes
2016-01-27T16:55:29.308+0000 check 9 25359
2016-01-27T16:55:29.409+0000 imported 25359 objects
```

##Contagem de Restaurantes

```
gkal19:~/workspace $ mongo be-mean
MongoDB shell version: 2.6.11
connecting to: be-mean
Mongo-Hacker 0.0.9
gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean> db.restaurantes.find({}).count()
25359
```
