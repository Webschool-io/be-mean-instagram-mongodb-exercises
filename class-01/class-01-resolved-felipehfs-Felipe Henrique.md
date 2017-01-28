# MongoDB - Aula 01 - Exercício
Autor: Felipe Henrique


## Importando os restaurantes
```
mongoimport --db be-mean -c restaurantes --drop --file restaurantes.json
2017-01-18T13:18:15.912-0200	connected to: localhost
2017-01-18T13:18:15.914-0200	dropping: be-mean.restaurantes
2017-01-18T13:18:18.826-0200	[###############.........] be-mean.restaurantes7.34MB/11.3MB (64.6%)
2017-01-18T13:18:20.295-0200	[########################] be-mean.restaurantes11.3MB/11.3MB (100.0%)
2017-01-18T13:18:20.295-0200	imported 25359 documents
```
## Contando os restaurantes
```
db.restaurantes.find({}).count()
25359
```
