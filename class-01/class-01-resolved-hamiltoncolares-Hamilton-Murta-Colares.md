# MongoDB - Aula 01 - Exerício
autor: Hamilton Murta Colares

## Importando os restaurantes

```
$ mongoimport --db be-mean-instagram --collection restaurantes --drop --file Documents/dev/be-mean-instagram/be-mean-instagram-mongodb/restaurantes.json
2015-12-10T11:58:47.488-0200	connected to: localhost
2015-12-10T11:58:47.489-0200	dropping: be-mean-instagram.restaurantes
2015-12-10T11:58:48.736-0200	imported 25359 documents
```
## Contando os restaurantes

```
MacBook-Pro-de-Hamilton-2(mongod-3.0.7) be-mean-instagram> db.restaurantes.find({}).count()
25359
```
