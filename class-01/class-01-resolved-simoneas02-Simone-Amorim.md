#MongoDB - Aula 01 - Exercício
Autor: Simone Amorim

##Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file C:\Users\simone\Documents\GitHub\be-mean-instagran\be-mean-instagram-mongodb-exercises\restaurantes.json
2016-01-31T20:21:41.929-0200    connected to: localhost
2016-01-31T20:21:41.933-0200    dropping: be-mean.restaurantes
2016-01-31T20:21:43.786-0200    imported 25359 documents
```

##Contando os restaurantes

```
C:\Users\simone>mongo
MongoDB shell version: 3.0.7
connecting to: test
use be-mean
switched to db be-mean
db.restaurantes.find({}).count()
25359
```