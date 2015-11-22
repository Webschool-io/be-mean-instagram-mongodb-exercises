# MongoDB - Aula 01 - Exercício
autor: Nurielly Caroline Brizola

## Importando os restaurantes

    ```
    
    mongoimport --db be_mean --collection restaurantes --drop --file restaurantes.json
    2015-11-22T21:33:46.514-0200    connected to: localhost
    2015-11-22T21:33:46.519-0200    dropping: be_mean.restaurantes
    2015-11-22T21:33:49.424-0200    [####################....] be_mean.restaurantes
    9.8 MB/11.4 MB (86.2%)
    2015-11-22T21:33:50.572-0200    imported 25359 documents
    
    ```

## Contando os restaurantes

    ```
    
    > use be_mean
    switched to db be_mean
    > db.restaurantes.find({}).count()
    25359
    >

    ```