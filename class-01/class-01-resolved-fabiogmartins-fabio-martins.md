#MongoDB - Aula 01 - Exericio
autor: Fabio Martins

##Importando os restaurantes

```
    mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
    connected to: 127.0.0.1
    2015-11-26T13:49:29.693-0200 dropping: be-mean.restaurantes
    2015-11-26T13:49:30.518-0200 check 9 25359
    2015-11-26T13:49:30.592-0200 imported 25359 objects
```
##Contando os restaurantes

```
    db.restaurantes.find({}).count()
    25359
```
