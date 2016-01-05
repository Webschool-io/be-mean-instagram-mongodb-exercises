# MongoDB - Aula 01 - Exercício
autor: MARLON WANGER

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file /home/marlonwanger/Downloads/restaurantes.json
    2015-11-19T18:17:25.955-0400    connected to: localhost
    2015-11-19T18:17:25.956-0400    dropping: be-mean.restaurantes
    2015-11-19T18:17:27.387-0400    imported 25359 documents


    ```

## Contando os restaurantes

    ```
    kakashicafe-PC(mongod-3.0.7) be-mean> db.restaurantes.find().count()
    25359


    ```