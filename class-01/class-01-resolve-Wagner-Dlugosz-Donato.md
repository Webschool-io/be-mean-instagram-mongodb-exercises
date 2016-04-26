# MongoDB - Aula 01 - Exercício
autor: Wagner Dlugosz Donato

## Importando os restaurantes

    ```
mongoimport --db be-mean-instagram --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2016-04-12T19:25:13.632-0300	connected to: 127.0.0.1
2016-04-12T19:25:13.633-0300	dropping: be-mean-instagram.restaurantes
2016-04-12T19:25:15.252-0300	imported 25359 documents

    
    ```

## Contando os restaurantes

    ```
    donato-dell(mongod-3.2.4) be-mean-instagram> db.restaurantes.find({}).count()
    25359


    ```
