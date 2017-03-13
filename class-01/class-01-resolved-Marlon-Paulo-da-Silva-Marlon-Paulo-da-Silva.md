# MongoDB - Aula 01 - Exercício
autor: Marlon Paulo da Silva

## Importando os restaurantes

    ```
     $ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
     2017-01-23T16:45:38.298-0200    connected to: 127.0.0.1
     2017-01-23T16:45:38.327-0200    dropping: be-mean.restaurantes
     2017-01-23T16:45:40.741-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find({}).count()
    25359
    ```