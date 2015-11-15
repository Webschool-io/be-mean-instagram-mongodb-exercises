# MongoDB - Aula 01 - Exercício
autor: Lucas Assis Vieira
## Importando os restaurantes

'''
PS C:\Users\Lucas Vieira\Pictures\MVs> mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-12T21:01:57.198-0200    connected to: localhost
2015-11-12T21:01:57.203-0200    dropping: be-mean.restaurantes
2015-11-12T21:01:59.637-0200    imported 25359 documents
'''

## Contando os restaurantes

'''
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359

'''