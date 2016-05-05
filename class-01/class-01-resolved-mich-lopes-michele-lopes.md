MongoDB - Aula 1 - Exercício 1

Autora: Michele Lopes

Importando os restaurantes

```
Herodice@Mich-Lopes MINGW64 ~/Desktop/PG/Be Mean/be-mean-instagram-mongodb/exercises/01 (master)
$ mongoimport --db be-mean --collection restaurentes --drop --file restaurantes.json
2015-11-19T13:14:16.282-0200    connected to: localhost
2015-11-19T13:14:16.284-0200    dropping: be-mean.restaurentes
2015-11-19T13:14:19.271-0200    [########################] be-mean.restaurentes11.4 MB/11.4 MB (100.0%)
2015-11-19T13:14:19.528-0200    imported 25359 documents
```

Contando os restaurantes

```
$ mongo
MongoDB shell version: 3.0.7
connecting to: test
Mongo-Hacker 0.0.4
use be-mean
switched to db be-mean
db
be-mean
db.restaurantes.find({}).count()
25359
```