# MongoDB - Aula 01 - Exercício
autor: Gustavo Gomes da Fé

## Importando os restaurantes

    ```
     mongmongoimport --db be-mean --collection restaurantes --drop --file /Volumes/SSD/Projects/Learning/BeMean/restaurantes.json
    2015-12-30T01:15:46.269-0200    connected to: localhost
    2015-12-30T01:15:46.270-0200    dropping: be-mean.restaurantes
    2015-12-30T01:15:47.521-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    Gustavos-Air(mongod-3.2.0) be-mean> db.restaurantes.find({}).count()
    25359

    ```