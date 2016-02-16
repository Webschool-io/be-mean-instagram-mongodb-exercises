# MongoDB - Aula 01 - Exercício
autor: Lucas Bento da Silva

## Importando os restaurantes

```
	mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2016-02-16T16:06:07.899-0200    connected to: localhost
    2016-02-16T16:06:07.901-0200    dropping: be-mean.restaurantes
    2016-02-16T16:06:10.860-0200    [########################] be-mean.restaurantes 11.3 MB/11.3 MB (100.0%)
    2016-02-16T16:06:10.865-0200    imported 25359 documents
```

## Contando os restaurantes

```
Command: db.restaurantes.find({}).count()
25359
>
```