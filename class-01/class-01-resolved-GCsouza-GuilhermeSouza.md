# MongoDB - Aula01 - Exercicio

# Importando os restaurantes

```
guilherme@guilherme-note:~$ mongoimport --db be-mean --collection restaurantes --file ~/Desktop/BE_MEAN/restaurantes.json
connected to: 127.0.0.1
Sat Dec  5 12:13:42.293 check 9 25359
Sat Dec  5 12:13:42.385 imported 25359 objects
```

# Contando os restaurantes
```
MongoDB shell version: 2.4.9
connecting to: test
Mongo-Hacker 0.0.9
guilherme-note(mongod-2.4.9) test> use be-mean
switched to db be-mean
guilherme-note(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```
