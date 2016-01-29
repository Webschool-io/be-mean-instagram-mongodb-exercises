# MongoDB - Aula 01 - Exercício
autor: JANYNNE GOMES

## Importando os restaurantes

    ```
    janynne@janynne-Lenovo-Ideapad-Flex14:~$ mongoimport --db be-mean --collection restaurantes --file github-projects/restaurantes.json 
    2015-12-01T01:20:29.822-0200    connected to: localhost
    2015-12-01T01:20:31.307-0200    imported 25359 documents

    ```

## Contando os restaurantes

    ```
    janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359

    ```