# mongoDB - Aula01 - exercicio

## importando os restaurantes
```
arthur@dv4-2040br:~/projects$ mongoimport --db be-mean --collection restaurantes --file restaurantes.json
connected to: 127.0.0.1
Sat Dec  5 12:10:07.459 check 9 25359
Sat Dec  5 12:10:07.506 imported 25359 objects
```

## contando os restaurantes
```
arthur@dv4-2040br:~/projects$ mongo
MongoDB shell version: 2.4.9
connecting to: test
Mongo-Hacker 0.0.9
dv4-2040br(mongod-2.4.9) test> use be-mean
switched to db be-mean
dv4-2040br(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25387
```
