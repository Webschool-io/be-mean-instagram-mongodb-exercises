
# MongoDB - Aula 01 - Exercício
autor: JOÃO PAULO EFFTING

## Importando os restaurantes

    ```
     mongoimport --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json 
     connected to: 127.0.0.1
     2016-04-07T20:13:10.330-0300 dropping: be-mean-instagram.restaurantes
     2016-04-07T20:13:11.496-0300 check 9 25359
     2016-04-07T20:13:11.759-0300 imported 25359 objects

    ```

## Contando os restaurantes

    ```
    joaopaulo(mongod-2.6.3) be-mean-instagram> db.restaurantes.find({}).count()
    25359

    ```