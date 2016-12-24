# MongoDB - Aula 01 - Exercício
autor: Lucas Taliberti

## Importando os restaurantes

    ```
    lucastaliberti@LucassMacBookPro:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json 
    2015-11-24T10:55:06.041-0200    connected to: localhost
    2015-11-24T10:55:06.042-0200    dropping: be-mean.restaurantes
    2015-11-24T10:55:06.954-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    LucassMacBookPro(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359

    ```