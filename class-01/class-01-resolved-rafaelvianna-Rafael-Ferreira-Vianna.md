# MongoDB - Aula 01 - Exercício
autor: Rafael Ferreira Vianna

## Importando os restaurantes

  ```
  $ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
  2016-11-01T12:03:34.181-0200    connected to: localhost
  2016-11-01T12:03:34.188-0200    dropping: be-mean.restaurantes
  2016-11-01T12:03:35.187-0200    imported 25359 documents

  ```

## Contando os restaurantes

  ```
  db.restaurantes.find({}).count()
  25359

   ```
