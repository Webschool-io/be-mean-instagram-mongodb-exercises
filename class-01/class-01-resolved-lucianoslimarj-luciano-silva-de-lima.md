# MongoDB - Aula 01 - Exercício
autor: Luciano Silva de Lima

## Importando os restaurantes

C:\dev\utis\Console2>mongoimport --db be-mean --collection restaurantes --drop --file C:/Cursos/webschool.io/restaurantes.json
2015-11-30T14:17:41.616-0200    connected to: localhost
2015-11-30T14:17:41.624-0200    dropping: be-mean.restaurantes
2015-11-30T14:17:44.597-0200    [##########..............] be-mean.restaurantes 5.2 MB/11.4 MB (45.5%)
2015-11-30T14:17:47.598-0200    [##########..............] be-mean.restaurantes 5.2 MB/11.4 MB (45.5%)
2015-11-30T14:17:50.597-0200    [##########..............] be-mean.restaurantes 5.2 MB/11.4 MB (45.5%)
2015-11-30T14:17:53.598-0200    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
2015-11-30T14:17:56.597-0200    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
2015-11-30T14:17:59.598-0200    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
2015-11-30T14:18:02.598-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2015-11-30T14:18:05.597-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2015-11-30T14:18:05.849-0200    imported 25359 documents
   

## Contando os restaurantes

> db.restaurantes.find().count()
25359
