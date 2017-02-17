# MongoDB - Aula 01 - Exercício
autor: Calleu Fuzi

## Importando os restaurantes

    ```
    MBP-de-Calleu:~ calleufuzi$ mongoimport --db be-mean --collection restaurantes --drop --file /Users/calleufuzi/Documents/restaurantes.json
    2017-02-17T18:26:07.344-0200	connected to: localhost
    2017-02-17T18:26:07.345-0200	dropping: be-mean.restaurantes
    2017-02-17T18:26:10.342-0200	[##############..........] be-mean.restaurantes	6.7 MB/11.4 MB (59.2%)
    2017-02-17T18:26:12.521-0200	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
    2017-02-17T18:26:12.522-0200	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    MBP-de-Calleu(mongod-3.2.8) test> use be-mean
    switched to db be-mean
    MBP-de-Calleu(mongod-3.2.8) be-mean> db.restaurantes.find({}).count()
    25359



    ```
