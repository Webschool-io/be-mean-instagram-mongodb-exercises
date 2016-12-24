# MongoDB - Aula 01 - Exercício
Autor: Paulo Daniel Carneiro

## Importando os restaurantes
```
mongoimport --db be-mean --collection restaurantes --file restaurantes.json                   
2016-09-07T18:27:23.536-0300    connected to: localhost
2016-09-07T18:27:26.515-0300    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.3%)
2016-09-07T18:27:26.940-0300    imported 25359 documents
```

## Contando os restaurantes
```
Paulo-PC(mongod-3.0.12) be-mean> db.restaurantes.find({}).count()
25359
```
