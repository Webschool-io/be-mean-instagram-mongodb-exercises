# MongoDB - Aula 01 - Exercício
autor: LUAN RAFAEL CASTOR PINHEIRO


## Importando os restaurantes

    ```
	luan@ubuntu-luan:~$ mongoimport --db be-mean --collection restaurantes --drop --file Documentos/restaurantes.json 
	2015-11-14T11:24:48.776-0200	connected to: localhost
	2015-11-14T11:24:48.776-0200	dropping: be-mean.restaurantes
	2015-11-14T11:24:51.779-0200	[####################....] be-mean.restaurantes	9.8 MB/11.4 MB (86.2%)
	2015-11-14T11:24:52.267-0200	imported 25359 documents

    ```

## Contando os restaurantes
	```
	db.restaurantes.find({}).count()
	25359
	```
