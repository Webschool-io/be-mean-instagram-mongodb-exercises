#MongoDB - Aula 01 - Exercício
auto: Emerson Chalegre

##Importando os restaurantes

[emerchalegre@emerchalegre class-01]$ mongoimport --db be-mean --collection restaurante --drop --file restaurantes.json 
2016-07-17T21:26:09.950-0300	connected to: localhost
2016-07-17T21:26:09.951-0300	dropping: be-mean.restaurante
2016-07-17T21:26:12.918-0300	[########################] be-mean.restaurante	11.4 MB/11.4 MB (100.0%)
2016-07-17T21:26:13.047-0300	imported 25359 documents

##Contando os restaurantes
> db.restaurantes.find({}).count()
25359
