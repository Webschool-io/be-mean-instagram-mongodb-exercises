# MongoDB - Aula 01 - Exercício
autor: Mário Mello

## Importando os restaurantes

```
➜  MongoDB mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-05-28T14:31:33.658-0300	connected to: localhost
2016-05-28T14:31:33.660-0300	dropping: be-mean.restaurantes
2016-05-28T14:31:34.783-0300	imported 25359 documents
```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359
```