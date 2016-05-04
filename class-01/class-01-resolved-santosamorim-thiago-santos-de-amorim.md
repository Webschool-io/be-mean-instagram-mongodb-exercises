# MongoDB - Aula 01 - Exercício
autor: THIAGO SANTOS DE AMORIM

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-02-20T09:11:00.441-0200    connected to: 127.0.0.1
2016-02-20T09:11:00.442-0200    dropping: be-mean.restaurantes
2016-02-20T09:11:03.440-0200    [#######################.] be-mean.restaurantes 11.2 MB/11.4 MB (99.0%)
2016-02-20T09:11:03.671-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-02-20T09:11:03.671-0200    imported 25359 documents
```

## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
>
``` 

