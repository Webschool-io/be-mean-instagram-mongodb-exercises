MongoDB - Aula 01 - Exercício
autor: Jadir J. Silva Junior

Importando os restaurantes

```
mick@ubuntu:~/Documents/Repos/be-mean-restaurantes$ mongoimport --db be-mean-restaurantes -c restaurantes --drop --file restaurantes.json
2015-11-27T00:00:15.907-0200    connected to: localhost
2015-11-27T00:00:15.908-0200    dropping: be-mean-restaurantes.restaurantes
2015-11-27T00:00:17.512-0200    imported 25359 documents

```
Contando os restaurantes

```
ubuntu(mongod-3.0.7) be-mean-restaurantes> db.restaurantes.find({}).count()
25359
```
