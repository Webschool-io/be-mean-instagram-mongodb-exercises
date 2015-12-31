# MongoDB - Aula 01 - Exercício
autor: Gabriel Tomé

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-21T03:02:30.230-0200 dropping: be-mean.restaurantes
2015-11-21T03:02:33.998-0200        Progress: 51985/11880943    0%
2015-11-21T03:02:33.998-0200            100 33/second
2015-11-21T03:02:36.218-0200        Progress: 2965160/11880943  24%
2015-11-21T03:02:36.218-0200            5500    916/second
2015-11-21T03:02:39.009-0200        Progress: 8378186/11880943  70%
2015-11-21T03:02:39.009-0200            15600   1733/second
2015-11-21T03:02:41.042-0200 check 9 25359
2015-11-21T03:02:41.249-0200 imported 25359 objects
```

## Contando os restaurantes

```
Gabriel-Tome(mongod-2.6.8) be-mean> db.restaurantes.find({}).count()
25359
```
