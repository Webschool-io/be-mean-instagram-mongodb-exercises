# MongoDB - Aula 01 - Exercício
autor: Jackson de Fraga

## Importando os restaurantes

 ```
Mac-mini-de-Jackson:class-01 jacksonfraga$ mongoimport --db bemean --collection restaurantes --drop --file /Users/jacksonfraga/Downloads/restaurantes.json
2016-03-25T18:18:04.473-0300    connected to: localhost
2016-03-25T18:18:04.473-0300    dropping: bemean.restaurantes
2016-03-25T18:18:05.265-0300    imported 25359 documents
Mac-mini-de-Jackson:class-01 jacksonfraga$ 
```

## Contando os restaurantes

```
Mac-mini-de-Jackson(mongod-3.0.5) bemean> db.restaurantes.find({}).count()
25359
Mac-mini-de-Jackson(mongod-3.0.5) bemean> 
```
