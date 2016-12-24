# MongoDB - Aula 01 - Exercício
autor: RAFAEL CARDOSO COELHO

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-27T23:44:08.570-0200    connected to: localhost
    2015-11-27T23:44:08.572-0200    dropping: be-mean.restaurantes
    2015-11-27T23:44:09.779-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find({}).count()
    25359

    ```