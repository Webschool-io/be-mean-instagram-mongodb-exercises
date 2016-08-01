# MongoDB - Aula 01 - Exercício
autor: Leonardo Gonçalves de Souza

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file ~/restaurantes.json 
2016-08-01T12:47:58.774-0300    connected to: localhost
2016-08-01T12:47:58.774-0300    dropping: be-mean.restaurantes
2016-08-01T12:48:00.916-0300    imported 25359 documents
```

## Contanto os restaurantes

```
 db.restaurantes.find({}).count()
25359
```
