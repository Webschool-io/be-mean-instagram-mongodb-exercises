# MongoDB - Aula 01 - Exercício
autor: GEISSON CARLOS ROSARIO DA SILVA

## Importando os restaurantes
```
PS C:\Users\PoRtelA> mongoimport --db mongodb --collection restaurantes --drop --file c:\restaurantes.json
2016-07-31T14:09:54.498-0300    connected to: localhost
2016-07-31T14:09:54.506-0300    dropping: mongodb.restaurantes
2016-07-31T14:09:57.518-0300    [##########..............] mongodb.restaurantes 5.2 MB/11.4 MB (45.5%)
2016-07-31T14:10:00.630-0300    [##########..............] mongodb.restaurantes 5.2 MB/11.4 MB (45.5%)
2016-07-31T14:10:03.417-0300    [###############.........] mongodb.restaurantes 7.4 MB/11.4 MB (65.5%)
2016-07-31T14:10:06.417-0300    [####################....] mongodb.restaurantes 9.8 MB/11.4 MB (86.2%)
2016-07-31T14:10:09.417-0300    [#######################.] mongodb.restaurantes 11.2 MB/11.4 MB (98.5%)
2016-07-31T14:10:10.562-0300    [########################] mongodb.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-07-31T14:10:10.563-0300    imported 25359 documents
```

## Contando os restaurantes
```
> db.restaurantes.find({}).count()
25359
```
