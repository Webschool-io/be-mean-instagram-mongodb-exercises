# MongoDB - Aula 01 - Exercício
autor: MATHEUS COSTA DE PAIVA

## Importando os restaurantes

    ```
	mate@levelho:~/Downloads$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	2015-12-10T21:50:11.649-0200	connected to: 127.0.0.1
	2015-12-10T21:50:11.714-0200	dropping: be-mean.restaurantes
	2015-12-10T21:50:14.453-0200	[################........] be-mean.restaurantes	7.7 MB/11.4 MB (67.9%)
	2015-12-10T21:50:15.422-0200	imported 25359 documents
    ```

## Contando os restaurantes

    ```
	MongoDB shell version: 3.0.7
	connecting to: test
	Mongo-Hacker 0.0.9
	levelho(mongod-3.0.7) test> show dbs
	local   → 0.078GB
	be-mean → 0.078GB
	test    → 0.078GB
	levelho(mongod-3.0.7) test> use be-mean
	switched to db be-mean
	levelho(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
	25359
    ```
