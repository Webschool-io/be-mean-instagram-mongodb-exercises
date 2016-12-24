# MongoDB - Aula 01 - Exercício
autor: Matheus Villalon

## Importando os restaurantes

    ```
     mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-01T17:14:32.283-0200	connected to: localhost
2016-01-01T17:14:32.284-0200	dropping: be-mean.restaurantes
2016-01-01T17:14:35.089-0200	[####################....] be-mean.restaurantes9.8 MB/11.3 MB (86.3%)
2016-01-01T17:14:35.926-0200	imported 25359 documents


    ```

## Contando os restaurantes

	> use be-mean
	switched to db be-mean
	> db.restaurantes.find({}).count()
	25359

