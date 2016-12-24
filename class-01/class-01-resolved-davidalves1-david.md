# MongoDB - Aula 1 - Exercício
autor: David Alves

## Importando os restaurantes

```
$ mongoimport --db test --collection restaurantes --host=127.0.0.1 --drop --file /Users/david/Downloads/restaurantes.json
2016-04-06T20:58:54.955-0300	connected to: 127.0.0.1
2016-04-06T20:58:54.956-0300	dropping: test.restaurantes
2016-04-06T20:58:57.947-0300	[########################] test.restaurantes	11.4 MB/11.4 MB (100.0%)
2016-04-06T20:58:58.114-0300	[########################] test.restaurantes	11.4 MB/11.4 MB (100.0%)
2016-04-06T20:58:58.114-0300	imported 25359 documents
```

## Contando os restaurantes
```
> db.restaurantes.find({}).count()
25359
```
