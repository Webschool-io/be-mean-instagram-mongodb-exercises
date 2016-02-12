# MongoDB - Aula 01 - Exercício
autor: Manoel Ricardo De Azevedo

## Importando os restaurantes
    
```
.\mongoimport.exe --db be-mean --collection restaurantes --drop --file C:\staurantes.json
2016-02-05T00:11:28.841-0200    connected to: localhost
2016-02-05T00:11:28.842-0200    dropping: be-mean.restaurantes
2016-02-05T00:11:29.785-0200    imported 25359 documents
```
    
## Contando os restaurantes
    
```
db.restaurantes.find({}).count()
25359
```
