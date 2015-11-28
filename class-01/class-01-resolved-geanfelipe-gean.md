
# MongoDB - Aula 01 - Exercício
autor: Gean Felipe

## Importando os restaurantes

    ```
 $ mongoimport --db bemean --collection restaurantes --drop --file ../be-mean-instagram-mongodb-excercises/class-01/restaurantes.json 
    2015-11-16T23:25:44.998-0300    connected to: localhost
    2015-11-16T23:25:45.000-0300    dropping: bemean.restaurantes
    2015-11-16T23:25:47.933-0300    [##########..............] bemean.restaurantes5.2 MB/11.4 MB (45.5%)
    2015-11-16T23:25:50.933-0300    [##########..............] bemean.restaurantes5.2 MB/11.4 MB (45.5%)
    2015-11-16T23:25:53.933-0300    [##########..............] bemean.restaurantes5.2 MB/11.4 MB (45.5%)
    2015-11-16T23:25:56.933-0300    [########################] bemean.restaurantes11.4 MB/11.4 MB (100.0%)
    2015-11-16T23:25:57.220-0300    imported 25359 documents


    ```

## Selecionando o banco de dados

    ```
    $ mongo bemean

    ```

## Contando os restaurantes

    ```
    debian(mongod-3.0.7) bemean> db.restaurantes.find({}).count()
    25359
    
    ```
