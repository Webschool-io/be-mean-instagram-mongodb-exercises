# MongoDB - Aula 01 - Exercício
autor: Cassiano Montanari

## Importando os restaurantes

    ```
    macmini:be-mean-mongodb-excercises cassianomon$ mongoimport --db database --collection restaurantes --drop --file restaurantes.json
	2016-05-30T14:44:05.464-0300	connected to: localhost
	2016-05-30T14:44:05.465-0300	dropping: database.restaurantes
	2016-05-30T14:44:08.315-0300	[##########..............] database.restaurante	5.2 MB/11.3 MB (45.5%)
	2016-05-30T14:44:11.315-0300	[##########..............] database.restaurante	5.2 MB/11.3 MB (45.5%)
	2016-05-30T14:44:14.315-0300	[####################....] database.restaurante	9.8 MB/11.3 MB (86.3%)
	2016-05-30T14:44:15.958-0300	[########################] database.restaurante	11.3 MB/11.3 MB (100.0%)
	2016-05-30T14:44:15.958-0300	imported 25359 documents
	macmini:be-mean-mongodb-excercises cassianomon$ 

    ```

## Contando os restaurantes

    ```
    > use database
	switched to db database
	> db.restaurantes.find({}).count()
	25359
	>
    X

    ```