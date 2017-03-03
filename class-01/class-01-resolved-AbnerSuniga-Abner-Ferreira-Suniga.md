# MongoDB - Aula 01 - Exercício
autor: Abner Ferreira Suniga

## Importando os restaurantes

    ```
    PS C:\Developer\mean> mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2016-09-10T10:02:51.366-0300    connected to: localhost
    2016-09-10T10:02:51.408-0300    dropping: be-mean.restaurantes
    2016-09-10T10:02:53.311-0300    imported 25359 documents
    PS C:\Developer\mean>

    ```

## Contando os restaurantes

    ```
    PS C:\Users\Abner> mongo
    2016-09-10T10:00:48.999-0300 I CONTROL  [main] Hotfix KB2731284 or later update is installed, will zero-out data files
    MongoDB shell version: 3.2.8
    connecting to: test
    > use be-mean
    switched to db be-mean
    > db.restaurantes.find({}).count()
    25359
    >
    ```