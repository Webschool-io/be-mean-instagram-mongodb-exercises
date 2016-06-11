
ngoDB - Aula 01 - Exercício
autor: Weslley Barros

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file ~/downloads/restaurantes.json
      2016-05-27T18:48:51.691-0300	connected to: localhost
      2016-05-27T18:48:51.695-0300	dropping: be-mean.restaurantes
      2016-05-27T18:48:54.164-0300	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    mongo be-mean
     MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> db.restaurantes.find({}).count()
     25359

    ```
