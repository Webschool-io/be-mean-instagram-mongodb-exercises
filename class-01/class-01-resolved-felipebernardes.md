# MongoDB - Aula01 - Exercicio

## Importando os restaurantes

```
bernardes@bernardes-laptop:~$ mongoimport --db be-mean --collection restaurantes --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 21 11:46:25.968 check 9 25359
Sat Nov 21 11:46:26.027 imported 25359 objects
```

## Contando os restaurantes

```
bernardes@bernardes-laptop:~$ mongo
MongoDB shell version: 2.4.9
connecting to: test
Mongo-Hacker 0.0.9
bernardes-laptop(mongod-2.4.9) test> use be-mean
switched to db be-mean
bernardes-laptop(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```
