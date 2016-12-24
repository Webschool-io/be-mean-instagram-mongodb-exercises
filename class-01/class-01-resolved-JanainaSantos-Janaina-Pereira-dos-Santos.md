# MongoDB - Aula 01 - Exercício
autor: Janaína P. dos Santos

## Importando os restaurantes
    PS C:\Users\Janaina\Desktop\be-mean-instagram-mongodb\MongoDb_01> mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2015-12-06T00:34:44.719-0200    connected to: localhost
	2015-12-06T00:34:44.721-0200    dropping: be-mean.restaurantes
	2015-12-06T00:34:46.438-0200    imported 25359 documents


## Contando os restaurantes
    > use be-mean
	switched to db be-mean
	> db.restaurantes.find({}).count()
	25359
	
	

 
 


