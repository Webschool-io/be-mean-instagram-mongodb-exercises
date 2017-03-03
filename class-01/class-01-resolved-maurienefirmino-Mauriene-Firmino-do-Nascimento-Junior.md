# MongoDB - Aula 01 - Exercício

Autor: Mauriene Firmino

## Importando os restaurantes

``` 
mauriene@mauriene-J1800NH:~$ mongoimport --db be-mean --collection restaurantes --file /home/mauriene/restaurantes.json
connected to: 127.0.0.1
2016-08-27T10:28:04.006-0300 		Progress: 11508437/11906303	96%
2016-08-27T10:28:04.006-0300 			23900	7966/second
2016-08-27T10:28:04.091-0300 check 9 25359
2016-08-27T10:28:04.162-0300 imported 25359 objects

```

## Contando os restaurantes

```
mauriene-J1800NH(mongod-2.6.10) be-mean> use be-mean
switched to db be-mean
mauriene-J1800NH(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
25359

```
