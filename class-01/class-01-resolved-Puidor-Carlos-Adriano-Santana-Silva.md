# MongoDB - Aula 01 - Exercício
autor: Carlos Adriano Santana Silva

## Importando os restaurantes

    ```
     $ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	 2015-11-16T19:01:17.175-0300    connected to: 127.0.0.1
	 2015-11-16T19:01:17.177-0300    dropping: be-mean.restaurantes
	 2015-11-16T19:01:18.971-0300    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
	25359

    ```
