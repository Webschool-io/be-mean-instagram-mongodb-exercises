# MongoDB - Aula 01 - Exercício
autor: Bruno Micaela

## Importando os restaurantes

    ```
    PS C:\> mongoimport --db be-mean --collection restaurantes --drop --file C:\Projects\be-mean-instagram-mongodb\restaurantes.json
	2015-11-14T19:20:39.184-0200    connected to: localhost
	2015-11-14T19:20:39.190-0200    dropping: be-mean.restaurantes
	2015-11-14T19:20:42.180-0200    [############............] be-mean.restaurantes 5.8 MB/11.4 MB (50.8%)
	2015-11-14T19:20:44.501-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
	25359

    ```

```