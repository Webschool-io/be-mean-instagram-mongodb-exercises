# MongoDB - Aula 01 - Exercício
autor: William Kraemer Aliaga

## Importando os restaurantes

    ```
	> mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2015-12-21T14:20:25.164-0200    connected to: localhost
	2015-12-21T14:20:25.176-0200    dropping: be-mean.restaurantes
	2015-12-21T14:20:26.824-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
	25359

    ```
