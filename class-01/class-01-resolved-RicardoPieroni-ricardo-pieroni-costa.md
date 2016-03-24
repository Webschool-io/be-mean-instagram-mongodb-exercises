# MongoDB - Aula 01 - Exercício
autor: Ricardo Pieroni Costa

##Importando os restaurantes

```
C:\Program Files\MongoDB\Server\3.2\bin>mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.js
on
2016-03-22T17:24:38.273-0300    connected to: localhost
2016-03-22T17:24:38.277-0300    dropping: be-mean.restaurantes
2016-03-22T17:24:41.265-0300    [###############.........] be-mean.restaurantes 7.2 MB/11.4 MB (63.4%)
2016-03-22T17:24:42.739-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-03-22T17:24:42.740-0300    imported 25359 documents
```

## Contando os restaurantes

```

C:\Program Files\MongoDB\Server\3.2\bin>mongo
MongoDB shell version: 3.2.4
connecting to: test

use be-mean
switched to db be-mean
db.restaurantes.find({}).count()
25359
```