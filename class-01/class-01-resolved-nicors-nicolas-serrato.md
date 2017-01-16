# MongoDB - Aula 01 - Exercício
autor: Nicolas Serrato

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
Sun Jan 15 21:41:04.285 dropping: be-mean.restaurantes
Sun Jan 15 21:41:06.013 check 9 25359
Sun Jan 15 21:41:06.120 imported 25359 objects
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
