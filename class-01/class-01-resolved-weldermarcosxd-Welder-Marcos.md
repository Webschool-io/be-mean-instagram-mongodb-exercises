# MongoDB - Aula 01 - Exercício
autor: Welder Marcos 

## Importando os restaurantes

```
welder@Welder-Mint ~/Documents/repos $ mongoimport --db db --collection restaurantes --drop --file ~/Desktop/restaurantes.json 
2015-12-12T12:47:05.927-0200	connected to: localhost
2015-12-12T12:47:05.927-0200	dropping: db.restaurantes
2015-12-12T12:47:07.044-0200	imported 25359 documents
```


## Contando os restaurantes

```
Welder-Mint(mongod-3.2.0) db> db.restaurantes.count()
25359

``

