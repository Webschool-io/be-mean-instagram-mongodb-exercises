#MongoDB - Aula 05 - Exercícios
autor: Thiago Nogueira

##1. Importar as collections restaurantes e pokemons
```js
~ ❯❯❯ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Desktop/pokemons.json                                                              2016-01-21T17:52:17.706-0300	connected to: 127.0.0.1
2016-01-21T17:52:17.707-0300	dropping: be-mean.pokemons
2016-01-21T17:52:17.851-0300	imported 610 documents
~ ❯❯❯ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Desktop/restaurantes.json                                2016-01-21T21:56:11.250-0300	connected to: 127.0.0.1
2016-01-21T21:56:11.251-0300	dropping: be-mean.restaurantes
2016-01-21T21:56:12.613-0300	imported 25359 documents
```
