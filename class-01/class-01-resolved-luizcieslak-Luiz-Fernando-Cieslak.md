# MongoDB - Aula 01 - Exercício
autor: Luiz Fernando Cieslak

## Importando os restaurantes

    ```
	mongoimport --db be-mean --collection restaurantes --drop --file ~/bemean/mongodb/restaurantes.json
	connected to: 127.0.0.1
	2016-09-13T22:18:08.037-0300 dropping: be-mean.restaurantes
	2016-09-13T22:18:08.488-0300 check 9 25359
	2016-09-13T22:18:08.498-0300 imported 25359 objects

    ```

## Contando os restaurantes

    ```
	luizcieslak-N150SD-N155SD(mongod-2.6.10) be-mean> db.restaurantes.find({}).count()
	25359
