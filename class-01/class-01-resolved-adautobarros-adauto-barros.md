# MongoDB - Aula 01 - Exercício
autor: José Adauto do Nascimento de Barros

## Importando os restaurantes

    ```
>mongoimport --db be-mean --collection restaurantes --host localhost:27017 --drop --file restaurantes.json
2015-11-12T14:55:13.386-0200    connected to: localhost:27017
2015-11-12T14:55:13.389-0200    dropping: be-mean.restaurantes
2015-11-12T14:55:14.857-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
   db.restaurantes.find({}).count()
   25359

    ```
