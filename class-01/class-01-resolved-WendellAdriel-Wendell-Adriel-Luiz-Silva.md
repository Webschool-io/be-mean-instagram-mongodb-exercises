# MongoDB - Aula 01 - Exercício

Autor: Wendell Adriel Luiz Silva

## Importando os restaurantes

  ```
  wendell@adamantium:~/Projetos/Webschool/BE MEAN$ mongoimport --db be-mean --collection restaurantes --drop --file ~/Projetos/Webschool/BE\ MEAN/restaurantes.json
  2015-11-19T23:25:00.510-0200	connected to: localhost
  2015-11-19T23:25:00.512-0200	dropping: be-mean.restaurantes
  2015-11-19T23:25:03.429-0200	[########################] be-mean.restaurantes	11.4 MB/11.4 MB (100.0%)
  2015-11-19T23:25:03.589-0200	imported 25359 documents
  ```
  
## Contando os restaurantes

  ```
  adamantium(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
  25359
  ```
