# MongoDB - Aula 01 - Exercício
autor: Rafael Gomes Cavalcanti

## Importando os restaurantes

	'''
	mongoimport --db be-mean --collection restaurantes --file restaurantes.json
	2016-08-31T23:56:48.503-0300    connected to: localhost
	2016-08-31T23:56:51.290-0300    [#################.......] be-mean.restaurantes 8.4 MB/11.4 MB (73.7%)
	2016-08-31T23:56:52.097-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
	2016-08-31T23:56:52.098-0300    imported 25359 documents
	'''

## Contando os restaurantes

    '''
    > db.restaurantes.find({}).count();
	25359
    '''