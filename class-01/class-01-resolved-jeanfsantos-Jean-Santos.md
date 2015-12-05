# MongoDB - Aula 01 - Exercício

Autor: Jean F. Santos

## Importando os restaurantes

  ```
  ➜  ~ mongoimport --db be-mean --collection restaurantes --drop --file ~/Development/bemean/data/restaurantes.json
  2015-11-14T15:16:50.521-0300	connected to: localhost
  2015-11-14T15:16:50.526-0300	dropping: be-mean.restaurantes
  2015-11-14T15:16:53.462-0300	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
  2015-11-14T15:16:53.628-0300	imported 25359 documents
  ```

## Contando os restaurantes

  ```
  MacBook-Pro-de-jean(mongod-3.0.7) test> use be-mean
  switched to db be-mean
  MacBook-Pro-de-jean(mongod-3.0.7) be-mean> db.restaurantes.find({}).count();
  25359
  ```
