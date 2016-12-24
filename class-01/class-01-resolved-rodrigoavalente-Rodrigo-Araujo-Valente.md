# MongoDB - Aula 01 - Exercício
autor: Rodrigo Valente

## Importando os restaurantes
```
mongoimport --db be-mean --collection restaurantes --drop --file home/data.json 
2015-12-29T20:08:47.215+0000    connected to: localhost
2015-12-29T20:08:47.215+0000    dropping: be-mean.restaurantes
2015-12-29T20:08:48.234+0000    imported 25359 documents
```

## Contando os restaurantes
```
db.restaurantes.find({}).count()
25359
```
