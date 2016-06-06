# MongoDB - Aula 01 - Exercício
autor: Luiz Henrique Soares

## Importando os restaurantes

    ```
C:\MongoDB\Server\3.2\bin
λ mongoimport --db be-mean --collection restaurantes  --host=127.0.0.1 --drop --file restaurantes.json
2016-06-06T16:31:35.127-0300    connected to: 127.0.0.1
2016-06-06T16:31:35.136-0300    dropping: be-mean.restaurantes
2016-06-06T16:31:38.121-0300    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.7%)
2016-06-06T16:31:38.598-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-06-06T16:31:38.600-0300    imported 25359 documents

    
    ```

## Contando os restaurantes

    ```
    > db.restaurantes.find().count()
	25359
	>
    ```
