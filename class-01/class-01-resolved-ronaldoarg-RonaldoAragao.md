# MongoDB - Aula 01 - Exercício
autor: Fco Ronaldo Aragão

## Importando os restaurantes

    ```
	$  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2015-11-12T18:58:30.157-0300	connected to: localhost
	2015-11-12T18:58:30.158-0300	dropping: be-mean.restaurantes
	2015-11-12T18:58:33.154-0300	[####################....] be-mean.restaurantes	9.8 MB/11.3 MB (86.3%)
	2015-11-12T18:58:33.795-0300	imported 25359 documents

    ```

## Contando os restaurantes

    ```
    be-mean> db.restaurantes.find({}).count()
    25359


    ```
