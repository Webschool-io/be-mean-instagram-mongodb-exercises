# MongoDB - Aula 01 - Exercício
Autor: Jonatas Leon

## Importando restaurantes

```
$ mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
2016-07-30T22:18:58.110-0300	connected to: localhost
2016-07-30T22:18:58.111-0300	dropping: be-mean.restaurantes
2016-07-30T22:18:59.326-0300	imported 25359 documents

```

## Contando os restaurantes

```
lucy(mongod-3.0.12) be-mean> db.restaurantes.find({}).count()
25359
```
