# MongoDB - Aula 01 - Exercicio
autor: Ronald Huggler

## Importando os restaurantes

  ```
  mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1  2015-11-21T11:13:11.426-0200 dropping: be-mean.restaurantes
2015-11-21T11:13:11.992-0200 check 9 25359
2015-11-21T11:13:12.080-0200 imported 25359 objects
  ```

## Contando os restaurantes

  ```
  Huggler-HP(mongod-2.6.11) be-mean> db.restaurantes.find({}).count()
25359
  ```
