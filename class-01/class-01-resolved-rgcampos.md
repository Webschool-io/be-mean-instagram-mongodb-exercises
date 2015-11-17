#MongoDB - Exercício 01

Autor: Renato Campos

#Importando dados

root@bemean:/# mongoimport --db test --collection restaurantes --drop --file /vagrant/be-mean/Aula01/restaurantes.json  
2015-11-17T01:27:02.873+0000    connected to: localhost  
2015-11-17T01:27:02.875+0000    dropping: test.restaurantes  
2015-11-17T01:27:05.866+0000    [############............] test.restaurantes    5.8 MB/11.3 MB (51.6%)  
2015-11-17T01:27:08.862+0000    [#######################.] test.restaurantes    11.3 MB/11.3 MB (99.9%)  
2015-11-17T01:27:09.053+0000    imported 25359 documents  

#Total de registros

root@bemean:/# mongo  
MongoDB shell version: 3.0.7  
connecting to: test  
bemean(mongod-3.0.7) test> db.restaurantes.find({}).count()  
25359  