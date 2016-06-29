# MongoDB - Aula 01 - Exercício
autor: Sóstenes freitas de Andrade (conta: sostenesfreitas)
 
## Importando os restaurantes
```
     mongoimport --db be_mean --collection restaurantes --drop --file restaurantes.json

    2016-02-24T13:35:04.835-0200	   connected to: localhost
	2016-02-24T13:35:04.835-0200	   dropping: be-mean.restaurantes
	2016-02-24T13:35:40.765-0300       [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
    2016-11-24T13:35:41.437-0300       [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
	2016-02-24T13:35:56.505-0200	   imported 25359 documents
```

## Contando os restaurantes
```
    BlackArch(mongod-3.2.1) be_mean> db.restaurantes.find({}).count()
    25359 
```
