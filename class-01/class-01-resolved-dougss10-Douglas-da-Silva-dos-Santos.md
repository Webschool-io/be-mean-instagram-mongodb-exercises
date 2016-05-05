# MongoDB - Aula 01 - Exercício
autor: Douglas da SIlva dos Santos

## Importando os restaurantes

	```

    C:\Users\Douglas>mongoimport --db be-mean --collection restaurantes --drop --fil
	e "c:/users/Douglas/Desktop/restaurantes.json"
	connected to: 127.0.0.1
	2015-11-09T23:52:50.980-0200 dropping: be-mean.restaurantes
	2015-11-09T23:52:53.007-0200            Progress: 10651198/11880944     89%
	2015-11-09T23:52:53.008-0200                    21200   7066/second
	2015-11-09T23:52:53.340-0200 check 9 25359
	2015-11-09T23:52:53.340-0200 imported 25359 objects

	```

## Contando os restaurantes

    ```
    C:\Users\Douglas>mongo
	MongoDB shell version: 2.6.10
	connecting to: test
	> use be-mean
	switched to db be-mean
	> db.restaurantes.find({}).count();
	25359
	>

    ```
