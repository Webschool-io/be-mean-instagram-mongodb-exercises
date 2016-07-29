# MongoDB - Aula 01 - Exercício
autor: Vitor Capretz

## Importando os restaurantes

```
mongoimport -db be-mean --collection restaurantes --drop --file Downloads/restaurantes.json 
connected to: 127.0.0.1
2016-05-23T19:07:53.389-0300 dropping: be-mean.restaurantes
2016-05-23T19:07:54.144-0300 check 9 25359
2016-05-23T19:07:54.289-0300 imported 25359 objects

```

## Contando os restaurantes

```
vitor-ThinkPad-T440(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
25359

```
