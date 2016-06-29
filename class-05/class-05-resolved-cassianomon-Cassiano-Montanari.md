# MongoDB - Aula 05 - Exercício
autor: Cassiano Montanari

## Importar as collections restaurantes e pokemons

	```
	C:\Users\Cassiano>mongoimport --host 127.0.0.1 --db be-mean-instagram --collection restaurantes --drop --file C:\Users\Cassiano\Dropbox\Dev\be-mean-instagram\restaurantes.json 
	2016-06-06T23:22:15.300-0300    connected to: 127.0.0.1
	2016-06-06T23:22:15.302-0300    dropping: be-mean-instagram.restaurantes
	2016-06-06T23:22:16.480-0300    imported 25359 documents


	C:\Users\Cassiano>mongoimport --host 127.0.0.1 --db be-mean-instagram --collection pokemons --drop --file C:\Users\Cassiano\Dropbox\Dev\be-mean-instagram\pokemons.json
	2016-06-06T23:22:46.827-0300    connected to: 127.0.0.1
	2016-06-06T23:22:46.828-0300    dropping: be-mean-instagram.pokemons
	2016-06-06T23:22:46.909-0300    imported 610 documents
	```

## Distinct por cuisine no db restaurantes 

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.restaurantes.distinct('cuisine')
	[
	  "Hamburgers",
	  "Bakery",
	  "Irish",
	  "American ",
	  "Jewish/Kosher",
	  "Ice Cream, Gelato, Yogurt, Ices",
	  "Delicatessen",
	  "Chinese",
	  "Chicken",
	  "Turkish",
	  "Caribbean",
	  "Donuts",
	  "Sandwiches/Salads/Mixed Buffet",
	  "Bagels/Pretzels",
	  "Pizza",
	  "Continental",
	  "Italian",
	  "Steak",
	  "Polish",
	  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
	  "German",
	  "French",
	  "Pizza/Italian",
	  "Mexican",
	  "Spanish",
	  "Café/Coffee/Tea",
	  "Tex-Mex",
	  "Pancakes/Waffles",
	  "Soul Food",
	  "Hotdogs",
	  "Greek",
	  "Seafood",
	  "Not Listed/Not Applicable",
	  "African",
	  "Japanese",
	  "Indian",
	  "Armenian",
	  "Thai",
	  "Chinese/Cuban",
	  "Mediterranean",
	  "Korean",
	  "Bottled beverages, including water, sodas, juices, etc.",
	  "Russian",
	  "Eastern European",
	  "Middle Eastern",
	  "Asian",
	  "Ethiopian",
	  "Vegetarian",
	  "Barbecue",
	  "Egyptian",
	  "English",
	  "Other",
	  "Sandwiches",
	  "Portuguese",
	  "Indonesian",
	  "Chinese/Japanese",
	  "Filipino",
	  "Juice, Smoothies, Fruit Salads",
	  "Brazilian",
	  "Afghan",
	  "Vietnamese/Cambodian/Malaysia",
	  "CafÃ©/Coffee/Tea",
	  "Soups & Sandwiches",
	  "Tapas",
	  "Moroccan",
	  "Pakistani",
	  "Peruvian",
	  "Bangladeshi",
	  "Czech",
	  "Salads",
	  "Creole",
	  "Fruits/Vegetables",
	  "Iranian",
	  "Cajun",
	  "Scandinavian",
	  "Polynesian",
	  "Soups",
	  "Australian",
	  "Hotdogs/Pretzels",
	  "Southwestern",
	  "Nuts/Confectionary",
	  "Hawaiian",
	  "Creole/Cajun",
	  "Californian",
	  "Chilean"
	]
	```
	
## Distinct por types no db pokemons 

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.distinct('types')
	[
	  "normal",
	  "fire",
	  "water",
	  "bug",
	  "flying",
	  "poison",
	  "electric",
	  "steel",
	  "ghost",
	  "ice",
	  "fighting",
	  "psychic",
	  "grass",
	  "ground",
	  "fairy",
	  "rock",
	  "dark",
	  "dragon"
	]
	```

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5) 

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*0)
	{
	  "name": "Rattata"
	}
	{
	  "name": "Charmeleon"
	}
	{
	  "name": "Wartortle"
	}
	{
	  "name": "Charmander"
	}
	{
	  "name": "Blastoise"
	}
	Fetched 5 record(s) in 5ms

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*1)
	{
	  "name": "Caterpie"
	}
	{
	  "name": "Metapod"
	}
	{
	  "name": "Butterfree"
	}
	{
	  "name": "Spearow"
	}
	{
	  "name": "Kakuna"
	}
	Fetched 5 record(s) in 6ms

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*2)
	{
	  "name": "Farfetchd"
	}
	{
	  "name": "Magnemite"
	}
	{
	  "name": "Magneton"
	}
	{
	  "name": "Seel"
	}
	{
	  "name": "Doduo"
	}
	Fetched 5 record(s) in 5ms
	```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo 

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.group({
	... initial: { total: 0},
	... reduce: function (curr, result){
	... curr.types.forEach(function(type){
	... if (result[type]) {
	... result[type]++;
	... } else {
	... result[type] = 1;
	... }
	... result.total++;
	... });
	... }
	... });
	[
	  {
	    "total": 915,
	    "normal": 78,
	    "fire": 47,
	    "water": 105,
	    "bug": 61,
	    "flying": 77,
	    "poison": 54,
	    "steel": 37,
	    "electric": 40,
	    "ghost": 34,
	    "ice": 24,
	    "fighting": 38,
	    "psychic": 62,
	    "grass": 75,
	    "ground": 51,
	    "fairy": 28,
	    "rock": 46,
	    "dark": 38,
	    "dragon": 20
	  }
	]
	```

## Realizar 3 counts na pokemons 

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.count({})
	610

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.count({types: 'fire'})
	47

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-instagram> db.pokemons.count({defense: {$gt: 70}})
	250
	```