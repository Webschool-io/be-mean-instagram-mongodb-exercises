# MongoDB - Aula 01 - Exercício
autor: JOABE LEONARD FEITOSA

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-04-13T01:06:53.202-0300    connected to: localhost
2016-04-13T01:06:53.205-0300    dropping: be-mean.restaurantes
2016-04-13T01:06:56.159-0300    [###################.....] be-mean.restaurantes
9.0 MB/11.4 MB (79.2%)
2016-04-13T01:06:57.787-0300    [########################] be-mean.restaurantes
11.4 MB/11.4 MB (100.0%)
2016-04-13T01:06:57.791-0300    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find({}).count()
    25359

    ```