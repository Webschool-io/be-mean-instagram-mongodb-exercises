# MongoDB - Aula 01 - Exercício
 Autor: Leonardo Larocca

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-26T02:39:36.306-0200    connected to: localhost
    2015-11-26T02:39:36.307-0200    dropping: be-mean.restaurantes
    2015-11-26T02:39:37.383-0200    imported 25359 documents

    ```
## Contando os restaurantes
    ```
    asus(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359

    ```
```

