# MongoDB - Aula 01 - Exercício
autor: Marcelo e Valdinei

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 21 11:10:34.147 check 9 25359
Sat Nov 21 11:10:34.311 imported 25359 objects
```

## Contando os restaurantes

```
  marcelo-K45A(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
25359
```
