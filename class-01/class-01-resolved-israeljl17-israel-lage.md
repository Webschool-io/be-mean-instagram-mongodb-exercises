# MongoDB - Aula 01 - Exercício
autor: ISRAEL LAGE

## Importando os restaurantes

    ```
    israeljl@israeljl-linux:~/Documents/learnMongoDB/be-mean-instagram-mongodb$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2016-07-18T20:30:44.468-0300	connected to: localhost
    2016-07-18T20:30:44.468-0300	dropping: be-mean.restaurantes
    2016-07-18T20:30:45.919-0300	imported 25359 documents


    ```

## Contando os restaurantes

    ```
    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359
    >


    ```
