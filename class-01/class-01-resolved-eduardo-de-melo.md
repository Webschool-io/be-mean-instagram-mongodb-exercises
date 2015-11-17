# MongoDB - Aula 01 - Exercício
autor: Eduardo de Melo

## Importando os restaurantes

```
Eduardo@Eduardo-PC MINGW32 ~/Desktop
$ mongoimport --db bemean --collection restaurantes --drop --file restaurantes.json
2015-11-16T23:23:15.329-0200    connected to: localhost
2015-11-16T23:23:15.331-0200    dropping: bemean.restaurantes
2015-11-16T23:23:17.432-0200    imported 25359 documents
```

## Contando os restaurantes

```
Eduardo@Eduardo-PC MINGW32 ~/Desktop
$ mongo bemean
MongoDB shell version: 3.0.7
connecting to: bemean
db.restaurantes.find({}).count()
25359
```