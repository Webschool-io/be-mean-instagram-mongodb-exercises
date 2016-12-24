# MongoDB - Aula 01 - Exercício
autor: Antonio Carlos da silva 

## Importando os restaurantes

```
$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 2016-10-02T01:33:58.711-0300	connected to: 127.0.0.1
2016-10-02T01:33:58.711-0300	dropping: be-mean.restaurantes
2016-10-02T01:33:59.279-0300	imported 25359 documents

```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
