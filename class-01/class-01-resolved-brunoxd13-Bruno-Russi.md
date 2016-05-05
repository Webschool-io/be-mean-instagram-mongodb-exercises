# MongoDB - Aula 01 - Exercício

Autor: Bruno Russi Lautenschlager

## Importando os restaurantes

``` shell
bruno@bruno-HP-ProBook-4530s:~/Documentos/Be_Mean$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-03-05T23:32:23.512-0300	connected to: localhost
2016-03-05T23:32:23.523-0300	dropping: be-mean.restaurantes
2016-03-05T23:32:25.236-0300	imported 25359 documents
```

## Contando os restaurantes

```
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
```

