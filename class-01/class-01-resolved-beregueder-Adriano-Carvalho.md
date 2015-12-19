# MongoDB - Aula 01 - Exercício
autor: Adriano Carvalho Batista

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2015-11-29T10:44:15.246-0200	connected to: 127.0.0.1
2015-11-29T10:44:15.247-0200	dropping: be-mean.restaurantes
2015-11-29T10:44:16.810-0200	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

 ```
