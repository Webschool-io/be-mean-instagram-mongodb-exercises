# MongoDB - Aula 01 - Exercício
autor: Leonardo Adriano de Souza

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json
    2016-01-11T00:53:59.202-0200	connected to: localhost
    2016-01-11T00:53:59.203-0200	dropping: be-mean.restaurantes
    2016-01-11T00:54:00.669-0200	imported 25359 documents    
    ```

## Contando os restaurantes

    ```
    wall-e(mongod-3.2.0) be-mean> db.restaurantes.count()
    25359

    ```
