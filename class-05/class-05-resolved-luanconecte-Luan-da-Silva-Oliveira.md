# MongoDB - Aula 05 - Exercício
autor: Luan da Silva Oliveira

## 1. Importar as collections restaurantes e pokemons

```
luanoliveira@luanoliveira ~/www $ ./mongo/bin/mongoimport --db be-mean --collection restaurantes --file restaurantes.json 
2015-11-22T20:00:36.291-0300	connected to: localhost
2015-11-22T20:00:38.129-0300	imported 25359 documents
luanoliveira@luanoliveira ~/www $ ./mongo/bin/mongoimport --db be-mean --collection pokemons --file pokemons.json 
2015-11-22T20:01:36.106-0300	connected to: localhost
2015-11-22T20:01:36.153-0300	imported 610 documents

luanoliveira(mongod-3.0.7) be-mean> show collections
pokemons       →  0.140MB /  0.164MB
restaurantes   → 14.012MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
```

## 2. Distinct por *cuisine* na restaurantes

```
luanoliveira(mongod-3.0.7) be-mean> db.restaurantes.distinct("cuisine")
[
  "Hamburgers",
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
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

## 3. Distinct por *types* na pokemons

```
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.distinct("types")
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5*0)
{
  "name": "Rattata"
}
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
Fetched 5 record(s) in 1ms
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5*1)
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
Fetched 5 record(s) in 2ms
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5*2)
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
  "name": "Doduo"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 2ms
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
db.pokemons.group({ 
	key: {  },
	reduce: function (curr, result) {
		curr.types.forEach(function(type) {
			if (result[type]) {
				result[type]++;
			} else {
				result[type] = 1;
			}
			result.total++;
		});
	},
	initial: { total: 0 } 
})
```

```
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.group({ 
... key: {  },
... reduce: function (curr, result) {
... curr.types.forEach(function(type) {
... if (result[type]) {
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... });
... },
... initial: { total: 0 } 
... })
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
    "ice": 24,
    "ghost": 34,
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

## 6. Realizar 3 counts na de pokemons

```
luanoliveira(mongod-3.0.7) be-mean> db.pokemons.count({})
610

luanoliveira(mongod-3.0.7) be-mean> db.pokemons.count({ attack: { $lt: 40 } })
582

luanoliveira(mongod-3.0.7) be-mean> db.pokemons.count({ attack: { $gt: 40 } })
534
```

:D