# MongoDB - Aula 01 - Exercício
autor: Camilo Costa Campos

## Importando os restaurantes

    ```
    wladek@ArchLinux ~: mongoimport --db be-mean --collection restaurantes --drop --host 127.0.0.1 --file  Downloads/restaurantes.json
    2015-12-08T19:34:35.616-0200    connected to: 127.0.0.1
    2015-12-08T19:34:35.616-0200    dropping: be-mean.restaurantes
    2015-12-08T19:34:37.192-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find({}).count()
    25359

    ```
