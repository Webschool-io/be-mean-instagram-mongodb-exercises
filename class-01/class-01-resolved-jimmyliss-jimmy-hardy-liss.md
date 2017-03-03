# MongoDB - Aula 01 - Exercício
autor: JIMMY HARDY LISS

## Importando os restaurantes
```
C:\Program Files\MongoDB\Server\3.2\bin>mongoimport --db be-mean --collection re
staurantes --drop --file restaurantes.json
2016-08-24T09:58:25.291-0300    connected to: localhost
2016-08-24T09:58:25.346-0300    dropping: be-mean.restaurantes
2016-08-24T09:58:27.557-0300    imported 25359 documents
```
## Contando os restaurantes
```
db.restaurantes.find({}).count()
25359
```