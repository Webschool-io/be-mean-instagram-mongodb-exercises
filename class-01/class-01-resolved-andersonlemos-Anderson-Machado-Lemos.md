# MongoDB - Aula 01 - Exercício
    autor: ANDERSON MACHADO LEMOS

## Importando os restaurantes

```
    [alemos@cerberus be-mean] $ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
    connected to: 127.0.0.1
    2016-02-16T23:36:59.007-0200 dropping: be-mean.restaurantes
    2016-02-16T23:37:00.135-0200 check 9 25359
    2016-02-16T23:37:00.671-0200 imported 25359 objects

```

## Contando os restaurantes

```

    cerberus(mongod-2.6.11) be-mean> db.restaurantes.find({}).count()
    25359


```


