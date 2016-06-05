# MongoDB - Aula 01 - Exercício
autor: Edison Magalhães Rocha

## Importando os restaurantes

    ```
    ╭─jr@njinga  ~  
    ╰─$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json                                                                         1 ↵
    2016-06-05T00:26:05.708-0300    connected to: localhost
    2016-06-05T00:26:05.708-0300    dropping: be-mean.restaurantes
    2016-06-05T00:26:06.955-0300    imported 25359 documents


    ```

## Contando os restaurantes

    ```
    njinga(mongod-3.2.6) test> use be-mean
    switched to db be-mean
    njinga(mongod-3.2.6) be-mean> db.restaurantes.find({}).count()
    25359

    ```