# MongoDB - Aula 01 - Exercício
autor: Fábio Calheiros (conta: fabiocalheiros)

## Importando os restaurantes

    ```
    fabio@fabio-Inspiron-7520:~/be-mean/aula01$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-15T17:18:18.196-0200    connected to: localhost
    2015-11-15T17:18:18.196-0200    dropping: be-mean.restaurantes
    2015-11-15T17:18:19.136-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    fabio-Inspiron-7520(mongod-3.0.7) test> use be-mean
    switched to db be-mean
    fabio-Inspiron-7520(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359

    ```