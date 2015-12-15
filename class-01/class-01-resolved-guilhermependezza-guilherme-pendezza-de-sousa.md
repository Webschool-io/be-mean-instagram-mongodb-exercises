#Autor: Guilherme Pendezza de Sousa

#Importando os restaurantes

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-08T03:46:57.181-0200	connected to: localhost
2015-12-08T03:46:57.181-0200	dropping: be-mean.restaurantes
2015-12-08T03:46:58.148-0200	imported 25359 documents


#Contando os restaurantes

guilherme-notebook(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
25359
