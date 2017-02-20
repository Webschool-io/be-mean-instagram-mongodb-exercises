# MongoDB - Aula 01 - Exercício
> Autor: Nil Késede

## Importando os restaurantes
```bash
> mongoimport --host=localhost --db be-mean --collection restaurantes --drop --file ./mongodb/data/restaurantes.json
2016-03-02T16:23:27.100-0300    connected to: localhost
2016-03-02T16:23:27.101-0300    dropping: be-mean.restaurantes
2016-03-02T16:23:28.923-0300    imported 25359 documents
```

## Contando os restaurantes
```js
> db.restaurantes.find().count()
25359
```
