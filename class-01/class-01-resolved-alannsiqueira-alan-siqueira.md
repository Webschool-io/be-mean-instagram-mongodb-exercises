# MongoDB - Aula 01 - Exercício
autor: Alan Siqueira

## Importando os restaurantes

```
C:\Users\alans>mongoimport --db be-mean --collection restaurantes --drop --file  C:\Users\alans\Desktop\restaurantes.json
2015-12-23T22:14:07.669-0200    connected to: localhost
2015-12-23T22:14:07.701-0200    dropping: be-mean.restaurantes
2015-12-23T22:14:10.565-0200    imported 25359 documents
 ```

## Contando os restaurantes

```
 C:\Users\alans>mongo be-mean
MongoDB shell version: 3.0.4
connecting to: be-mean
> db.restaurantes.find({}).count()
25359
    ```