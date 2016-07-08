# MongoDB - Aula 01 - Exercício
autor: Karoline Lemos

## Importando os restaurantes 
...

$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-07-08T17:44:25.265-0300    connected to: localhost
2016-07-08T17:44:25.266-0300    dropping: be-mean.restaurantes
2016-07-08T17:44:26.863-0300    imported 25359 documents

...

## Contando os restaurantes 

...

arrffs(mongod-3.2.7) be-mean> db.restaurantes.find({}).count()
25359

...