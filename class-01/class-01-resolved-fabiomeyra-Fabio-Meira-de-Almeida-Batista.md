# MongoDB - Aula 01 - Exercício
autor: Fábio Meira

## Importando os restaurantes

    ```
    mongoimport -d be-mean -c restaurantes --drop --file /Users/fabiomeyra/Desktop/restaurantes.json
	2016-12-16T20:46:40.646-0200	connected to: localhost
	2016-12-16T20:46:40.647-0200	dropping: be-mean.restaurantes
	2016-12-16T20:46:42.481-0200	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    suissacorp(mongod-3.0.6) be-mean> db.restaurantes.find({}).count()
    25359

    ```