# MongoDB - Aula 01 - Exercício
autor: Ronaldo Paggi

## Importando os restaurantes

    ```
    (MongoDb) ➜ () ➜ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2016-03-10T20:40:47.169-0300    connected to: localhost
    2016-03-10T20:40:47.170-0300    dropping: be-mean.restaurantes
    2016-03-10T20:40:50.173-0300    [##########..............] be-mean.restaurantes 5.2 MB/11.4 MB (45.5%)
    2016-03-10T20:40:53.162-0300    [###################.....] be-mean.restaurantes 9.3 MB/11.4 MB (81.7%)
    2016-03-10T20:40:55.354-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
    2016-03-10T20:40:55.355-0300    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    (MongoDb) ➜ () ➜ mongo be-mean
    MongoDB shell version: 3.2.4
    connecting to: be-mean
    > db.restaurantes.find({}).count()
    25359
    > 

    ```