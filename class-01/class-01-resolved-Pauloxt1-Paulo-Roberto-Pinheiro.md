# MongoDB - Aula 01 - Exercício
Autor: Paulo Roberto

## Importando os restaurantes
```
$ mongoimport --db be-mean --collection restaurantes --drop --file C:/restaurantes.json
2015-12-23T15:10:06.838-0200    connected to: localhost
2015-12-23T15:10:06.840-0200    dropping: be-mean.restaurantes
2015-12-23T15:10:08.756-0200    imported 25359 documents
```
## Contando os restaurantes
```
2015-12-23T15:13:56.302-0200 I CONTROL  [main] Hotfix KB2731284 or later update
is not installed, will zero-out data files
MongoDB shell version: 3.2.0
connecting to: test
use be-mean
switched to db be-mean
db.restaurantes.find({}).count()
25359
```
