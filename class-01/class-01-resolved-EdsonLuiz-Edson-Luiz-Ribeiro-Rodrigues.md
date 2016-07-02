# MongoDB - Aula 01 - Exercício
autor: Edson Luiz Ribeiro Rodrigues

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-07-01T23:45:20.794-0300	connected to: localhost
2016-07-01T23:45:20.796-0300	dropping: be-mean.restaurantes
2016-07-01T23:45:22.452-0300	imported 25359 documents
```

## Contando os restaurantes

```
mac(mongod-3.2.7) be-mean> db.restaurantes.find({}).count()
25359
```
