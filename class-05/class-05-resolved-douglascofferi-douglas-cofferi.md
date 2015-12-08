# MongoDB - Aula 05 - Exercício
autor: Douglas Cofferi

## 1. Importar as collections restaurantes e pokemons
```
	mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json 
	2015-11-22T20:32:53.208-0200	connected to: 127.0.0.1
	2015-11-22T20:32:53.209-0200	dropping: be-mean.restaurantes
	2015-11-22T20:32:56.207-0200	[##################......] be-mean.restaurantes	8.8 MB/11.3 MB (78.1%)
	2015-11-22T20:32:57.888-0200	imported 25359 documents
	mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Downloads/pokemons.json 
	2015-11-22T20:33:38.071-0200	connected to: 127.0.0.1
	2015-11-22T20:33:38.115-0200	dropping: be-mean.pokemons
	2015-11-22T20:33:38.235-0200	imported 610 documents
```
## 2. Distinct por 'cuisine' na restaurantes 
```
	> db.restaurantes.distinct('cuisine').sort()
	[
	  "Afghan",
	  "African",
	  "American ",
	  "Armenian",
	  "Asian",
	  "Australian",
	  "Bagels/Pretzels",
	  "Bakery",
	  "Bangladeshi",
	  "Barbecue",
	  "Bottled beverages, including water, sodas, juices, etc.",
	  "Brazilian",
	  "CafÃ©/Coffee/Tea",
	  "Café/Coffee/Tea",
	  "Cajun",
	  "Californian",
	  "Caribbean",
	  "Chicken",
	  "Chilean",
	  "Chinese",
	  "Chinese/Cuban",
	  "Chinese/Japanese",
	  "Continental",
	  "Creole",
	  "Creole/Cajun",
	  "Czech",
	  "Delicatessen",
	  "Donuts",
	  "Eastern European",
	  "Egyptian",
	  "English",
	  "Ethiopian",
	  "Filipino",
	  "French",
	  "Fruits/Vegetables",
	  "German",
	  "Greek",
	  "Hamburgers",
	  "Hawaiian",
	  "Hotdogs",
	  "Hotdogs/Pretzels",
	  "Ice Cream, Gelato, Yogurt, Ices",
	  "Indian",
	  "Indonesian",
	  "Iranian",
	  "Irish",
	  "Italian",
	  "Japanese",
	  "Jewish/Kosher",
	  "Juice, Smoothies, Fruit Salads",
	  "Korean",
	  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
	  "Mediterranean",
	  "Mexican",
	  "Middle Eastern",
	  "Moroccan",
	  "Not Listed/Not Applicable",
	  "Nuts/Confectionary",
	  "Other",
	  "Pakistani",
	  "Pancakes/Waffles",
	  "Peruvian",
	  "Pizza",
	  "Pizza/Italian",
	  "Polish",
	  "Polynesian",
	  "Portuguese",
	  "Russian",
	  "Salads",
	  "Sandwiches",
	  "Sandwiches/Salads/Mixed Buffet",
	  "Scandinavian",
	  "Seafood",
	  "Soul Food",
	  "Soups",
	  "Soups & Sandwiches",
	  "Southwestern",
	  "Spanish",
	  "Steak",
	  "Tapas",
	  "Tex-Mex",
	  "Thai",
	  "Turkish",
	  "Vegetarian",
	  "Vietnamese/Cambodian/Malaysia"
	]
```

## 3. Distinct por 'types' na pokemons
```
	> db.pokemons.distinct('types').sort()
	[
	  "bug",
	  "dark",
	  "dragon",
	  "electric",
	  "fairy",
	  "fighting",
	  "fire",
	  "flying",
	  "ghost",
	  "grass",
	  "ground",
	  "ice",
	  "normal",
	  "poison",
	  "psychic",
	  "rock",
	  "steel",
	  "water"
	]

```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
	> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
	{
	  "name": "Charmander"
	}
	{
	  "name": "Charmeleon"
	}
	{
	  "name": "Wartortle"
	}
	{
	  "name": "Blastoise"
	}
	{
	  "name": "Caterpie"
	}
	Fetched 5 record(s) in 1ms
	> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
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
	{
	  "name": "Farfetchd"
	}
	Fetched 5 record(s) in 1ms
	> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
	{
	  "name": "Magnemite"
	}
	{
	  "name": "Magneton"
	}
	{
	  "name": "Doduo"
	}
	{
	  "name": "Seel"
	}
	{
	  "name": "Dodrio"
	}
	Fetched 5 record(s) in 2ms
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo 
```
	> db.pokemons.aggregate([
	...     { 
	...     $unwind: "$types" 
	...     },
	...     { 
	...     $group: {
	...           _id: "$types",
	...           count: { $sum : 1 }
	...         }
	...     }
	... ])
	{
	  "result": [
	    {
	      "_id": "fairy",
	      "count": 28
	    },
	    {
	      "_id": "psychic",
	      "count": 62
	    },
	    {
	      "_id": "fighting",
	      "count": 38
	    },
	    {
	      "_id": "dark",
	      "count": 38
	    },
	    {
	      "_id": "ground",
	      "count": 51
	    },
	    {
	      "_id": "grass",
	      "count": 75
	    },
	    {
	      "_id": "electric",
	      "count": 40
	    },
	    {
	      "_id": "steel",
	      "count": 37
	    },
	    {
	      "_id": "rock",
	      "count": 46
	    },
	    {
	      "_id": "flying",
	      "count": 77
	    },
	    {
	      "_id": "fire",
	      "count": 47
	    },
	    {
	      "_id": "ice",
	      "count": 24
	    },
	    {
	      "_id": "bug",
	      "count": 61
	    },
	    {
	      "_id": "poison",
	      "count": 54
	    },
	    {
	      "_id": "normal",
	      "count": 78
	    },
	    {
	      "_id": "ghost",
	      "count": 34
	    },
	    {
	      "_id": "dragon",
	      "count": 20
	    },
	    {
	      "_id": "water",
	      "count": 105
	    }
	  ],
	  "ok": 1
	}
```

## 6. Realizar 3 counts na pokemons
```
	> db.pokemons.count()
	610
	> var query = {types: {$in: [/fire/i]}}
	> query
	{
	  "types": {
	    "$in": [
	      /fire/i
	    ]
	  }
	}
	> db.pokemons.find(query).count()
	47
	> var query = {defense: {$gt: 70}}
	> query
	{
	  "defense": {
	    "$gt": 70
	  }
	}
	> db.pokemons.find(query).count()
	250
```