# MongoDB - Aula 01 - Exercício
autor: Ederson Devaldo da Silva

## Importando os restaurantes
```
mongoimport --host=127.0.0.1 -d be-mean -c restaurantes --drop --file restaurantes.json
2015-12-04T02:53:49.814-0200    connected to: 127.0.0.1
2015-12-04T02:53:49.816-0200    dropping: be-mean.restaurantes
2015-12-04T02:53:52.796-0200    [#####################...] be-mean.restaurantes 10.4 MB/11.4 MB (91.6%)
2015-12-04T02:53:53.117-0200    imported 25359 documents
```
## Contando os restaurantes
```
> db.restaurantes.find({}).count()
25359
```
