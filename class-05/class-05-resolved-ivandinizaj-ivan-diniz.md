# MongoDB - Aula 05- Exercício
autor: Ivan Diniz


## 1. Importar as collections `restaurantes` e `pokemons`.

```JS
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json 

2015-12-28T00:24:18.026-0300	connected to: 127.0.0.1
2015-12-28T00:24:18.027-0300	dropping: be-mean.pokemons
2015-12-28T00:24:18.877-0300	imported 610 documents

$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
2015-12-28T00:26:13.883-0300	connected to: 127.0.0.1
2015-12-28T00:26:13.884-0300	dropping: be-mean.restaurantes
2015-12-28T00:26:16.585-0300	imported 25359 documents
```

## 2. Distinct por `cuisine` na restaurantes.

```JS
$db.restaurantes.distinct('cuisine')

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
  "Continental",
  "Pizza",
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
  "Seafood",
  "Hotdogs",
  "Greek",
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

## 3-  Distinct por `types` na pokemons.

```JS
$ db.pokemons.distinct('types')

[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "electric",
  "steel",
  "poison",
  "ice",
  "ghost",
  "psychic",
  "fighting",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]

```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```JS
$ var amount = 5
$ var current = 0;
$ var query = {}
$ var fields = {_id: 0, name: 1}

$ db.pokemons.find(query, fields).limit(amount).skip(amount * ++current);
$ db.pokemons.find(query, fields).limit(amount).skip(amount * ++current);
$ db.pokemons.find(query, fields).limit(amount).skip(amount * ++current);

```
## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```JavaScript
//Group
$ db.pokemons.group({
	initial: {},
	reduce: function(curr, result){
		curr.types.forEach(function(type){
			result[type] = result[type] ? result[type] + 1 : 1 ;
		});	
	}
});

[
  {
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "steel": 37,
    "electric": 40,
    "poison": 54,
    "ice": 24,
    "ghost": 34,
    "psychic": 62,
    "fighting": 38,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]

//Aggregate

db.pokemons.aggregate([
	{ $unwind: '$types' },
	{
		$group: {
			_id : '$types',
			count: {$sum : 1}
		}
	}
]);

"waitedMS": NumberLong("0"),
"result": [
{
  "_id": "grass",
  "count": 75
},
{
  "_id": "dark",
  "count": 38
},
{
  "_id": "fairy",
  "count": 28
},
{
  "_id": "psychic",
  "count": 62
},
{
  "_id": "ice",
  "count": 24
},
{
  "_id": "ground",
  "count": 51
},
{
  "_id": "poison",
  "count": 54
},
{
  "_id": "electric",
  "count": 40
},
{
  "_id": "dragon",
  "count": 20
},
{
  "_id": "bug",
  "count": 61
},
{
  "_id": "steel",
  "count": 37
},
{
  "_id": "ghost",
  "count": 34
},
{
  "_id": "rock",
  "count": 46
},
{
  "_id": "water",
  "count": 105
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
  "_id": "fighting",
  "count": 38
},
{
  "_id": "normal",
  "count": 78
}
]

```
## 6. Realizar `3` counts na pokemons.

```JS
$ var query = { defense : {$gte: 50}, attack : {$gte: 50} }
$ db.pokemons.count(query);

412

$ var query = {hp: {$gte: 70}}
$ db.pokemons.count(query)

271

$ var query = {types: /fire/i, attack: {$gte: 50}}
$ db.pokemons.count(query)

42
```