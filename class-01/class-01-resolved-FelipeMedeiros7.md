# MongoDB - Aula 01 - Exercício
autor: Felipe Medeiros de Lacerda

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes <restaurantes.json.txt 
2016-10-17T11:58:26.625-0200    connected to: localhost 
2016-10-17T11:58:28.045-0200    imported 25359 documents
```

## Contando os restaurantes

```
smigu@LAPTOP-LJMEQ9O6 C:\MongoDB\Server\3.2\bin 
$ mongo MongoDB shell version: 3.2.10 
connecting to: test 
> use be-mean 
switched to db be-mean 
> db.restaurantes.find({}).count() 
25359

```