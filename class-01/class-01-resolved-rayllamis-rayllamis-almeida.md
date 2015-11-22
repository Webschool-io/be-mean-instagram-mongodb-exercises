# MongoDB - Aula 01 - Exercício
autor: Rayllamis Almeida

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file ~/Dropbox/be-mean-instagram/MongoDB/Exercicios/Aula\ 1/restaurantes.json
    2015-11-15T16:45:59.076-0300    connected to: 127.0.0.1
    2015-11-15T16:45:59.077-0300    dropping: be-mean.restaurantes
    2015-11-15T16:46:00.079-0300    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find().count()
    25359

    ```