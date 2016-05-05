# MongoDB - Aula 01 - Exercício
autor: Icaro Caldeira (https://github.com/icarcal)

## Importando os restaurantes

```js
vagrant@vagrant-ubuntu-trusty-64:/vagrant$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-14T22:04:36.362+0000    connected to: localhost
2015-11-14T22:04:36.362+0000    dropping: be-mean.restaurantes
2015-11-14T22:04:38.544+0000    imported 25359 documents

```

## Contando os restaurantes

```js
vagrant@vagrant-ubuntu-trusty-64:/vagrant$ mongo
MongoDB shell version: 3.0.7
connecting to: test
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
> 

```