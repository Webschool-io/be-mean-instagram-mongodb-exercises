# MongoDB - Aula 01 - Exercício
autor: Renato Galvão

## Importando os restaurantes

```
GalvonesBook:repos renatogalvao$ mongoimport --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json
2016-02-13T18:11:59.608-0200    connected to: localhost
2016-02-13T18:11:59.609-0200    dropping: be-mean.restaurantes
2016-02-13T18:12:01.443-0200    imported 25359 documents

```

## Trocando de banco

```
> use be-mean
switched to db be-mean

```

## Contando os restaurantes

```

> db.restaurantes.find({}).count()
25359

```
