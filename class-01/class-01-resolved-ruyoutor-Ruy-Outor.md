# MongoDB - Aula 01 - Exercício
```
autor: Ruy Outor
```

## Importando os restaurantes

```js
> ruyoutor:~/workspace $ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-08-02T19:19:10.977+0000    connected to: localhost
2016-08-02T19:19:10.978+0000    dropping: be-mean-instagram.restaurantes
2016-08-02T19:19:12.844+0000    imported 25359 documents
```

## Contando os restaurantes

```js
> db.restaurantes.find({}).count()
25359
```