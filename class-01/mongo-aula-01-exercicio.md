# MongoDB - Aula 01 - Exercício
autor: Sóstenes freitas de andrade

## Importando os restaurantes

    ```
     mongoimport --db be_mean --collection restaurantes --drop --file restaurantes.json

    	2016-02-18T17:35:04.835-0200	connected to: localhost
	2016-02-18T17:35:04.835-0200	dropping: be_mean.restaurantes
	2016-02-18T17:35:06.505-0200	Failed: error processing document #16211: unexpected EOF
	2016-02-18T17:35:06.505-0200	imported 0 documents

    ```

## Contando os restaurantes

    ```
    BlackArch(mongod-3.2.1) be_mean> db.restaurantes.find({}).count()
    10000


    ```