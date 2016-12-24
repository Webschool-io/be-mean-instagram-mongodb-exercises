# MongoDB - Aula 01 - Exercício
autor: Eduardo Pinheiro Quaresma Castro

## Importando os restaurantes
```js
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-29T16:55:18.410-0300    connected to: localhost
2016-01-29T16:55:18.411-0300    dropping: be-mean.restaurantes
2016-01-29T16:55:19.837-0300    imported 25359 documents
```
## Contando os restaurante
```js
Cybertron(mongod-3.0.9) be-mean> db.restaurantes.count({})
25359
```