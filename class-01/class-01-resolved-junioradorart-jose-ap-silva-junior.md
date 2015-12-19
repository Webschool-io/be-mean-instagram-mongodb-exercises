# MongoDB - Aula 01 - Exercício
autor: JOSE AP SILVA JUNIOR

## Importando os restaurantes

	```
	mongoimport --db be-mean --collection restaurantes --drop --file C:\aulas-mongo\restaurantes.json
	connected to: 127.0.0.1
	2015-11-10T16:46:47.089-0300 dropping: be-mean.restaurantes
	2015-11-10T16:46:50.002-0300            Progress: 3667667/11880944      30%
	2015-11-10T16:46:50.002-0300                    6800    2266/second
	2015-11-10T16:46:53.033-0300            Progress: 8125177/11880944      68%
	2015-11-10T16:46:53.034-0300                    15100   2516/second
	2015-11-10T16:46:56.010-0300            Progress: 11659431/11880944     98%
	2015-11-10T16:46:56.011-0300                    24500   2722/second
	2015-11-10T16:46:56.277-0300 check 9 25359
	2015-11-10T16:46:56.278-0300 imported 25359 objects

	```

## Contando os restaurantes

	```
	mongo be-mean db.restaurantes.find({}).count()
	25359

	```
