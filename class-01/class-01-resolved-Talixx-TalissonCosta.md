# MongoDB - Aula 01 - Exercício
autor: Tálisson Costa

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
    2015-12-09T16:24:05.530-0200    connected to: localhost
    2015-12-09T16:24:05.531-0200    dropping: be-mean.restaurantes
    2015-12-09T16:24:08.218-0200    imported 25359 documents


    ```

## Contando os restaurantes

    ```
use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25362

    ```