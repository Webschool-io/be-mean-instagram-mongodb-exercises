# MongoDB - Aula 05 - Exercício
autor: Jose Ap. Silva Junior

## 1. Importar as collections restaurantes e pokemons.

```
> mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file C:\aulas-mongo\pokemons.
json
connected to: 127.0.0.1
2015-11-27T13:09:03.868-0300 dropping: be-mean.pokemons
2015-11-27T13:09:04.123-0300 check 9 610
2015-11-27T13:09:04.124-0300 imported 610 objects

```

## 2. Distinct por `cuisine` na restaurantes.

```
> db.restaurantes.distinct("cuisine").sort()
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

## 3-  Distinct por types na pokemons.

```
> db.pokemons.distinct("types").sort()
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
> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5 * 0)
{ "name" : "Rattata" }
{ "name" : "Charmander" }
{ "name" : "Charmeleon" }
{ "name" : "Wartortle" }
{ "name" : "Blastoise" }

> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5 * 1)
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5 * 2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
> db.pokemons.group({
		initial: {total: 0},
		reduce: function(curr, result){
			curr.types.forEach(function(type){
				if(result[type]){
					result[type]++;
				}else{
					result[type] = 1;
				}
				result.total++;
			});
		}
	})

	[
		{
			"total" : 915,
			"normal" : 78,
			"fire" : 47,
			"water" : 105,
			"bug" : 61,
			"flying" : 77,
			"poison" : 54,
			"steel" : 37,
			"electric" : 40,
			"ice" : 24,
			"ghost" : 34,
			"fighting" : 38,
			"psychic" : 62,
			"grass" : 75,
			"ground" : 51,
			"fairy" : 28,
			"rock" : 46,
			"dark" : 38,
			"dragon" : 20
		}
	]
```

## 6. Realizar 3 counts na pokemons.
```
> db.pokemons.count()
610

> db.pokemons.count({types: 'fire'})
47

> db.pokemons.count({defense: {$gt: 70}})
250

```
