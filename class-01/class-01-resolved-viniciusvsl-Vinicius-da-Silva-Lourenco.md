# MongoDB - Aula 01 - Exercício
autor: Vinicius da Silva Lourenço

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-09T18:25:36.226-0300	connected to: localhost
2016-02-09T18:25:36.227-0300	dropping: be-mean.restaurantes
2016-02-09T18:25:37.235-0300	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find().count()
25359
```
