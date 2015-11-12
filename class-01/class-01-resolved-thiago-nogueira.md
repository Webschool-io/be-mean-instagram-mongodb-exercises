# MongoDB - Aula 01 - Exercício
autor: Thiago Nogueira

## Importando os restaurantes

  ```
  ~/d/bemean ❯❯❯ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
  2015-11-12T16:58:42.554-0300	connected to: localhost
  2015-11-12T16:58:42.555-0300	dropping: be-mean.restaurantes
  2015-11-12T16:58:44.181-0300	imported 25359 documents

  ```
## Contando os restaurantes

  ```

  TNP-MacBook-Air(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
  25359

  ```
