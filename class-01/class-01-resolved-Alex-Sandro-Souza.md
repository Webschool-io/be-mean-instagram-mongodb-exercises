# MongoDB - Aula 01 - Exercício
autor: Alex Sandro Souza

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2017-10-30T20:01:06.908-0200	connected to: localhost
2017-10-30T20:01:06.909-0200	dropping: be-mean.restaurantes
2017-10-30T20:01:07.969-0200	imported 25359 documents

```

## Contando os restaurantes

```
gigantus(mongod-3.2.17) be-mean> db.restaurantes.find({}).count()
25359
```
