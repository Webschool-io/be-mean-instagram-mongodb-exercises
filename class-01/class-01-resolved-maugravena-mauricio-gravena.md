# MongoDB - Aula 01 - Exercício
autor: Mauricio Gravena de Oliveira

## Importando os restaurantes

```
➜  ~  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-13T11:23:16.502-0200    connected to: localhost
2015-11-13T11:23:16.503-0200    dropping: be-mean.restaurantes
2015-11-13T11:23:19.148-0200    imported 25359 documents
```

## Contando os restaurantes

```
mau-desktop(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
```
