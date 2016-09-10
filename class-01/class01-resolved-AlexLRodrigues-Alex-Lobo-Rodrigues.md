# MongoDB - Aula 01 - Exercício
autor: Alex Lobo Rodrigues

## Importando os restaurantes

    ```
mongoimport --db be-mean --collection restaurantes --drop --file dados.json
connected to: 127.0.0.1
Fri Aug 19 17:12:16.705 dropping: be-mean.restaurantes
Fri Aug 19 17:12:17.349 check 9 25359
Fri Aug 19 17:12:17.426 imported 25359 objects

    ```

## Contando os restaurantes

    ```
db.restaurantes.find({}).count()
25359

    ```
