# MongoDB - Aula 01 - Exercício
autor: José Maria Monteiro Junior

## Importando os restaurantes

    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-12-01T15:09:51.765-0200    connected to: localhost
    2015-12-01T15:09:51.766-0200    dropping: be-mean.restaurantes
    2015-12-01T15:09:52.710-0200    imported 25359 documents


## Contando os restaurantes

    > db.restaurantes.find({}).count()
    25359
