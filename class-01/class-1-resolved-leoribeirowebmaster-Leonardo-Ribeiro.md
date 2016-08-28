#MongoDB - Aula 01 - Exercício#

##Autor: Leonardo Ribeiro##

###Importando os restaurantes###

```
mongoimport mongoimport -d be-mean -c restaurantes --drop --file /restaurantes.json
2016-07-11T01:54:55.360-0300 connected to: localhost
2016-07-11T01:54:55.361-0300 dropping: be-mean.restaurantes
2016-07-11T01:54:55.970-0300 imported 25359 documents
```

###Contando os restaurantes###
```
db.restaurantes.find({}).count()
25359
```