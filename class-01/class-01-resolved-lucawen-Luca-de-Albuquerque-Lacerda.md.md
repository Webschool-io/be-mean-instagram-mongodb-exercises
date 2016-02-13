# MongoDB - Aula 01 - Exercício
autor: Luca Albuquerque

## Importando os restaurantes

    ```
	 mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	connected to: 127.0.0.1
	2016-02-13T17:18:04.263+0000 dropping: be-mean.restaurantes
	2016-02-13T17:18:06.178+0000 check 9 25359
	2016-02-13T17:18:06.178+0000 imported 25359 objects

    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
	25359

    ```
