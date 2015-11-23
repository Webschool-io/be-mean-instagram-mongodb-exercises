# MongoDB - Aula 01 - Exercício
autor: Eduardo Chaves

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-20T17:56:06.534-0200	connected to: localhost
    2015-11-20T17:56:06.536-0200	dropping: be-mean.restaurantes
    2015-11-20T17:56:08.132-0200	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    2015-11-20 17:56:08 ☆  Eduardo-Chaves in ~/Downloads
    ○ → mongo
    MongoDB shell version: 3.0.7
    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359
    > 

    ```
