# MongoDB - Aula 01 - Exercício
autor: LEONARDO SOUZA

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-26T00:39:30.397-0200    connected to: localhost
    2015-11-26T00:39:30.397-0200    dropping: be-mean.restaurantes
    2015-11-26T00:39:31.619-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > show dbs
    > use be-mean
    > db.restaurantes.find({}).count()
    25359

    ```