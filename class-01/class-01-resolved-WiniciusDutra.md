# MongoDB - Aula 01 - Exercício
autor: Vinicius Dutra

## Importando os restaurantes

    ```
    C:\Program Files\MongoDB\Server\3.2\bin>mongoimport --db     be-mean --collection restaurantes --drop --file c:\restaurantes.json
    2017-01-27T20:42:41.653-0200    connected to: localhost
    2017-01-27T20:42:41.668-0200    dropping: be-mean.restaurantes
    2017-01-27T20:42:43.282-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359

    ```
