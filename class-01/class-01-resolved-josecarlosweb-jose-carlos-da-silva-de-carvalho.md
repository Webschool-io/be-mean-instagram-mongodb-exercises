# MongoDB - Aula 01 - Exercício
autor: JOSE CARLOS DA SILVA DE CARVALHO

## Importando os restaurantes

    ```
	carlos@carlos-pc:~$ mongoimport --db database --collection collection --drop --file Documentos/Curso\ BeMEAN/restaurantes.json 
	connected to: 127.0.0.1
	Wed Nov 11 22:05:53.859 dropping: database.collection
	Wed Nov 11 22:05:54.316 check 9 25359
	Wed Nov 11 22:05:54.406 imported 25359 objects
	carlos@carlos-pc:~$ 

    ```

## Contando os restaurantes

    ```
	carlos@carlos-pc:~$ mongo
	MongoDB shell version: 2.4.9
	connecting to: test
	Mongo-Hacker 0.0.8
	carlos-pc(mongod-2.4.9) test> show dbs
	local     0.078GB
	database  0.203GB
	bemean    0.203GB
	be-mean   (empty)
	carlos-pc(mongod-2.4.9) test> use bemean
	switched to db bemean
	carlos-pc(mongod-2.4.9) bemean> db.restaurantes.find({}).count()
	25359
	carlos-pc(mongod-2.4.9) bemean> 

    ```
