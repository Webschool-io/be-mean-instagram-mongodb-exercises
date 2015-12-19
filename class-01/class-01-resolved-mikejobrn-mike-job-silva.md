# MongoDB - Aula 01 - Exercício
autor: Mike Job Santos Pereira da Silva

## Importando os restaurantes

    ```
    mongoimport --db be-mean --collection restaurantes --drop --file data/restaurantes.json 
    connected to: 127.0.0.1
    Thu Nov 12 22:36:10.157 dropping: be-mean.restaurantes
    Thu Nov 12 22:36:10.714 check 9 25359
    Thu Nov 12 22:36:11.050 imported 25359 objects
    ```

## Contando os restaurantes

    ```
    Mike-Notebook(mongod-2.4.9) be-mean> db.restaurantes.find({}).count()
    25359
    ```

