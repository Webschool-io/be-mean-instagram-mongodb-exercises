# MongoDB - Aula 01 - Exerc�cio
autor: Leonardo Ferreira Vilela

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --file  C:/Temp/restaurantes.json
2015-11-15T11:28:43.502-0200    connected to: localhost
2015-11-15T11:28:43.507-0200    dropping: be-mean.restaurantes
2015-11-15T11:28:45.683-0200    imported 25359 documents
```


## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
>
```
