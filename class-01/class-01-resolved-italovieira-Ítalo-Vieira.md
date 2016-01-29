# MongoDB - Aula 01 - Exercício
autor: Ítalo Vieira

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-22T12:40:42.155-0300	connected to: 127.0.0.1
    2015-11-22T12:40:42.156-0300	dropping: be-mean.restaurantes
    2015-11-22T12:40:43.222-0300	imported 25359 documents
    ```

## Contando os restaurantes

    ```
    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359
