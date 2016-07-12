# MongoDB - Aula 01 - Exercício
autor: Felipe Rodrigues Alves

## Importando os restaurantes

```
felipealves@Ubuntu16lts:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-05-27T19:59:01.301-0400    connected to: localhost
2016-05-27T19:59:01.302-0400    dropping: be-mean.restaurantes
2016-05-27T19:59:04.302-0400    [######################..] be-mean.restaurantes 10.7 MB/11.4 MB (94.6%)
2016-05-27T19:59:04.491-0400    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-05-27T19:59:04.491-0400    imported 25359 documents
```

## Contando os restaurantes

```
Ubuntu16lts(mongod-3.2.6) be-mean> db.restaurantes.find({}).count()
25359
```
