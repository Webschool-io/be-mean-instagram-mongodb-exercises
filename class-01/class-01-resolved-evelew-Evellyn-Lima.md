


# MongoDB - Aula 01 - Exercício
autor: EVELLYN LIMA

## Importando os restaurantes

	mongoimport --db be-mean --collection restaurantes --drop --file "C:\Users\Evellyn Lima\Documents\mongodb\restaurantes.json"
    2016-12-03T21:04:06.946-0200    connected to: localhost
	2016-12-03T21:04:06.985-0200    dropping: be-mean.restaurantes
	2016-12-03T21:04:09.862-0200    [########################] be-mean.restaurantes 11.3MB/8.11MB (140.0%)
	2016-12-03T21:04:11.125-0200    [########################] be-mean.restaurantes 11.3MB/11.3MB (100.0%)
	2016-12-03T21:04:11.126-0200    imported 25359 documents


## Contando os restaurantes

	use be-mean
    db.restaurantes.find({}).count()
    25359
