# MongoDB - Aula 01 - Exercício
autor: Renan Gabriel Almeida Silva

## Importando os restaurantes

    ```
      mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    connected to: 127.0.0.1
    2016-07-13T14:57:20.432-0300 dropping: be-mean.restaurantes
    2016-07-13T14:57:21.033-0300 check 9 25359
    2016-07-13T14:57:21.071-0300 imported 25359 objects
    ```

## Contando os restaurantes

    ```
    note(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
    25359
    ```
