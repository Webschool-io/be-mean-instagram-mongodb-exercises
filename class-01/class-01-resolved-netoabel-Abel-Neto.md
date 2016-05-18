# MongoDB - Aula 01 - Exercício
User: [netoabel](http://www.github.com/netoabel)

Autor: Abel Neto

```
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-05-04T14:51:05.946-0300	connected to: localhost
2016-05-04T14:51:05.947-0300	dropping: be-mean.restaurantes
2016-05-04T14:51:07.366-0300	imported 25359 documents
```

## Contando os restaurantes

```
be-mean> db.restaurantes.find({}).count()
25359
```
