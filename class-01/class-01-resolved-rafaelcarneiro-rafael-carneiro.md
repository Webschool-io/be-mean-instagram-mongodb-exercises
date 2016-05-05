# MongoDB - Aula 01 - Exercício
autor: Rafael Carneiro

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2015-12-03T01:17:38.917-0300    connected to: localhost
	2015-12-03T01:17:38.918-0300    dropping: be-mean.restaurantes
	2015-12-03T01:17:40.878-0300    imported 25359 documents
    ```

## Contando os restaurantes

    ```
	SKYNET(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.restaurantes.find({}).count()
	25359
    ```