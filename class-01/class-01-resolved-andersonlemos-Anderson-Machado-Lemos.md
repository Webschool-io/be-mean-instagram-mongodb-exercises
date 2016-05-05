# MongoDB - Aula 01 - Exercício
    autor: ANDERSON MACHADO LEMOS

## Importando os restaurantes

```
[alemos@cerberus be-mean]$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2016-02-17T10:20:12.144-0200 dropping: be-mean.restaurantes
2016-02-17T10:20:12.892-0200 check 9 25359
2016-02-17T10:20:13.613-0200 imported 25359 objects

```

## Contando os restaurantes

```
cerberus(mongod-2.6.11) be-mean> db.restaurantes.find({}).count()
25359

```

