# MongoDB - Aula 01 - Exercício
autor: Luan Henrique Santos Simões de Almeida

## Importando os restaurantes

```
(master ?:1 ✗) exercices mongoimport --db bemean --collection restaurantes --drop --file ./restaurantes.json
2016-05-21T17:41:19.697-0300	connected to: localhost
2016-05-21T17:41:19.698-0300	dropping: bemean.restaurantes
2016-05-21T17:41:21.795-0300	imported 25359 documents
```

## Contando os restaurantes

```
inspiron(mongod-3.2.6) bemean> db.restaurantes.find({}).count()
25359
```
