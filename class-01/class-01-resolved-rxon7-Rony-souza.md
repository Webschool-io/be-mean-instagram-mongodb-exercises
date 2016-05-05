# MongoDB - Aula 01 - Exercício
autor: Ronyclay Barreto de Souza

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
connected to: 127.0.0.1
Wed Nov 11 19:01:49.879 dropping: be-mean.restaurantes
Wed Nov 11 19:01:51.213 check 9 25359
Wed Nov 11 19:01:51.511 imported 25359 objects
```

## Contando os restaurantes

```
use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25362
```
