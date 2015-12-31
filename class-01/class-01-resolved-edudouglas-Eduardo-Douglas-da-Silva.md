# MongoDB - Aula 01 - Exercício
autor: Eduardo Douglas da Silva

```
➜  exercises  mongoimport --db be-mean -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 14 11:23:29.020 dropping: be-mean.restaurantes
Sat Nov 14 11:23:29.457 check 9 25359
Sat Nov 14 11:23:29.483 imported 25359 objects
```

# Contando os restaurantes
```
> use be-mean
switched to db be-mean

> db.restaurantes.find({}).count()
25359
```
