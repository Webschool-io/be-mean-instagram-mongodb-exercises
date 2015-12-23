# MongoDB - Aula 01 - Exercício
Autor: Paulo Roberto

## Importando os restaurantes
```
$ mongoimport --db be-mean --collection restaurantes --drop --file C:/restaurantes.json<br>
2015-12-23T15:10:06.838-0200    connected to: localhost<br>
2015-12-23T15:10:06.840-0200    dropping: be-mean.restaurantes<br>
2015-12-23T15:10:08.756-0200    imported 25359 documents
```
## Contando os restaurantes
```
2015-12-23T15:13:56.302-0200 I CONTROL  [main] Hotfix KB2731284 or later update<br>
is not installed, will zero-out data files<br>
MongoDB shell version: 3.2.0<br>
connecting to: test<br>
use be-mean<br>
switched to db be-mean<br>
db.restaurantes.find({}).count()<br>
25359
```
