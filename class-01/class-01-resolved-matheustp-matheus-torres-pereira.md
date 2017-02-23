# MongoDB - Aula 01 - Exercício
autor: Matheus Torres Pereira

## Importando os restaurantes

```
matt@ubuntu ~/mongodb> mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
2017-02-23T02:24:53.654-0300    connected to: 127.0.0.1
2017-02-23T02:24:53.654-0300    dropping: be-mean.restaurantes
2017-02-23T02:24:55.445-0300    imported 25359 documents
```

## Contando os restaurantes

```
> db.restaurantes.find({}).count()
25359
```