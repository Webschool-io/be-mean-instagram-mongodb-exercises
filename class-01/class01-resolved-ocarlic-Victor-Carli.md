# MongoDB - Aula 01 - Exercício
autor: Victor Carli

## Importando os restaurantes

    ```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
connected to: 127.0.0.1
2017-02-11T17:11:38.907-0200 dropping: be-mean.restaurantes
2017-02-11T17:11:41.011-0200 		Progress: 9475074/11906303	79%
2017-02-11T17:11:41.011-0200 			18000	6000/second
2017-02-11T17:11:41.518-0200 check 9 25359
2017-02-11T17:11:41.640-0200 imported 25359 objects

    ```
## Contando os restaurantes

    ```
db.restaurantes.find({}).count()
25359

    ```
