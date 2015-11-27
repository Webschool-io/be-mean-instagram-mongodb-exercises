# MongoDB - Aula 01 - Exercício
autor: Camilla Tres

## Importando os restaurantes

    mongoimport --db be-mean --collection restaurantes --drop --file /home/camilla/projetos/be-mean-exercicios/restaurantes.json
    2015-11-16T00:43:22.683-0200	connected to: localhost
    2015-11-16T00:43:22.684-0200	dropping: be-mean.restaurantes
    2015-11-16T00:43:23.662-0200	imported 25359 documents

## Contando os restaurantes

    camilla-Mean(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359
