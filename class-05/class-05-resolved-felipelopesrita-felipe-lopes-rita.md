# MongoDB - Aula 05 - Exercício
User: [felipelopesrita]https://github.com/felipelopesrita
Autor: Felipe José Lopes Rita

# Importar as collections `restaurantes` e `pokemons`.
Feito :p

# Distinct por `cuisine` na restaurantes.
```js
StarKiller(mongod-3.2.0) be-mean> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "American ",
  "Irish",
  "Jewish/Kosher",
  "Delicatessen",
  "Bakery",
  "Ice Cream, Gelato, Yogurt, Ices",
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
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Polish",
  "French",
  "German",
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

# Distinct por `types` na pokemons.
```js
StarKiller(mongod-3.2.0) be-mean> db.pokemons.distinct('types')
[
  "grass",
  "poison",
  "fire",
  "flying",
  "water",
  "bug",
  "normal",
  "electric",
  "ground",
  "fairy",
  "fighting",
  "psychic",
  "rock",
  "steel",
  "ice",
  "ghost",
  "dragon",
  "dark"
]
```

# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```js
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({}).limit(5).skip(5 * 0)
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({}).limit(5).skip(5 * 1)
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({}).limit(5).skip(5 * 2)
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
StarKiller(mongod-3.2.0) be-mean> db.pokemons.group({
	initial: { },
	reduce: function( current, result ) {
		current.types.forEach(function(tipo){
			if( result[tipo] )
				result[tipo] += 1;
			else
				result[tipo] = 1;
		})
	}
})

[
  {
    "poison": 57,
    "grass": 74,
    "fire": 44,
    "flying": 75,
    "water": 108,
    "bug": 57,
    "normal": 85,
    "electric": 36,
    "ground": 54,
    "fairy": 22,
    "fighting": 34,
    "psychic": 67,
    "rock": 46,
    "steel": 32,
    "ice": 25,
    "ghost": 25,
    "dragon": 20,
    "dark": 32
  }
]
```

# Realizar 3 counts na pokemons.
```js
StarKiller(mongod-3.2.0) be-mean> db.pokemons.count()
610
StarKiller(mongod-3.2.0) be-mean> db.pokemons.count({types: 'rock'})
46
StarKiller(mongod-3.2.0) be-mean> db.pokemons.count({types: 'fire'})
44
```