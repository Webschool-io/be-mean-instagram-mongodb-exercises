# MongoDB - Aula 01 - Exercício
autor: Bruno Novais

## Importando os restaurantes

  ```
  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
  2015-11-22T15:43:29.074-0200    connected to: localhost
  2015-11-22T15:43:29.084-0200    dropping: test.restaurantes
  2015-11-22T15:43:31.795-0200    [##########..............] test.restaurantes    5.2 MB/11.3 MB (45.5%)
  2015-11-22T15:43:34.795-0200    [####################....] test.restaurantes    9.8 MB/11.3 MB (86.3%)
  2015-11-22T15:43:37.795-0200    [####################....] test.restaurantes    9.8 MB/11.3 MB (86.3%)
  2015-11-22T15:43:39.952-0200    imported 25359 documents
  ```

## Contando os restaurantes

  ```
  > db.restaurantes.find({}).count()
  25359
  ```
