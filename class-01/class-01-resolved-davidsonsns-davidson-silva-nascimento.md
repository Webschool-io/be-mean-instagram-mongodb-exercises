# MongoDB - Aula 01 - Exercício
autor: Davidson da Silva Nascimento

## Importando os restaurantes

    DavidsonSilva@DAVIDSON ~/beMean/be-mean-instagram-mongodb/exercises (master)
    $ mongoimport --db be-mean --collection restaurantes --drop restaurantes.json
    2015-11-12T01:03:04.072-0200    connected to: localhost
    2015-11-12T01:03:04.075-0200    dropping: be-mean.restaurantes
    2015-11-12T01:03:05.968-0200    imported 25359 documents
    
## Contando os restaurantes

    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359
    