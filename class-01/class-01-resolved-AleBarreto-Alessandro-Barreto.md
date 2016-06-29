# MongoDB - Aula 01 - Exercício
autor: Alessandro Barreto

## Importando os restaurantes

    ```
     mongoimport [mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json]
        2016-06-13T21:58:05.036-0400    connected to: 127.0.0.1
        2016-06-13T21:58:05.046-0400    dropping: be-mean.restaurantes
        2016-06-13T21:58:08.029-0400    [############............] be-mean.restaurantes
        5.9 MB/11.4 MB (52.3%)
        2016-06-13T21:58:10.569-0400    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
    25359
    >


    ```