# MongoDB - Aula 01 - Exercício
autor: **Pablo Zaniolo**

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurants --host 127.0.0.1 --drop --file restaurants.json
    2016-05-02T15:46:25.340-0300    connected to: 127.0.0.1
    2016-05-02T15:46:25.340-0300    dropping: be-mean.restaurants
    2016-05-02T15:46:26.484-0300    imported 25359 documents
    ```

## Contando os restaurantes

    ```
    db.restaurants.find({}).count()
    25359
    ```