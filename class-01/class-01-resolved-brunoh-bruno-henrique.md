# MongoDB - Aula 01 - Exercício
Autor: Bruno Henrique C. da Silva

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-12-24T13:22:25.271-0200    connected to: localhost
    2015-12-24T13:22:25.272-0200    dropping: be-mean-instagram.restaurantes
    2015-12-24T13:22:27.951-0200    [#######################.] be-mean-instagram.restaurantes   11.0 MB/11.4 MB (96.7%)
    2015-12-24T13:22:28.137-0200    imported 25359 documents
    ```

## Contando os restaurantes

    ```
    brunoh(mongod-3.0.7) be-mean> db.restaurantes.find().count()
    25359
    ```