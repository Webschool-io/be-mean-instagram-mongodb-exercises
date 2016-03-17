# MongoDB - Aula 01 - Exercício
autor: ERIC LESSA

## Importando os restaurantes

    ```
    mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
    2016-03-15T17:27:43.372-0300	connected to: localhost
    2016-03-15T17:27:43.372-0300	dropping: be-mean.restaurantes
    2016-03-15T17:27:44.703-0300	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    ericlessa(mongod-3.2.4) be-mean> db.restaurantes.find({}).count();
    25359

    ```
