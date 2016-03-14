# MongoDB - Aula 05 - Exercício
autor: Marcos Dias da Conceição

# 1. Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json
connected to: 127.0.0.1
2016-02-07T18:07:11.726-0300 dropping: be-mean.restaurantes
2016-02-07T18:07:12.143-0300 check 9 25359
2016-02-07T18:07:12.392-0300 imported 25359 objects

mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Downloads/pokemons.json
connected to: 127.0.0.1
2016-02-07T18:12:48.892-0300 dropping: be-mean.pokemons
2016-02-07T18:12:48.908-0300 check 9 620
2016-02-07T18:12:48.908-0300 imported 620 objects
```

# 2. Distinct por `cuisine` na restaurantes
```
db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
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

# 3. Distinct por `types` na pokemons
```
db.pokemons.distinct('types')
[
  "bug",
  "poison",
  "flying",
  "normal",
  "electric",
  "water",
  "fighting",
  "psychic",
  "grass",
  "fairy",
  "fire",
  "rock",
  "ice",
  "ground",
  "steel",
  "ghost",
  "dark",
  "dragon"
]
```

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
db.pokemons.find().limit(5).skip(5 * 0);
db.pokemons.find().limit(5).skip(5 * 1);
db.pokemons.find().limit(5).skip(5 * 2);
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
db.pokemons.group({
	initial: {total: 0},
	reduce: function(current, result) {
		current.types.forEach(function(type){
			if(result[type]) {
				result[type]++;
			} else {
				result[type] = 1;
			}
			result.total++;
		})
	}
})
[
  {
    "total": 934,
    "poison": 54,
    "bug": 58,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "water": 101,
    "fighting": 42,
    "psychic": 61,
    "grass": 70,
    "fairy": 31,
    "fire": 53,
    "rock": 42,
    "ice": 28,
    "ground": 53,
    "steel": 35,
    "ghost": 34,
    "dark": 35,
    "dragon": 30
  }
]
```

# 6. Realizar 3 counts na pokemons
```
db.pokemons.find().count()
620
db.pokemons.find({types: 'fire'}).count()
53
db.pokemons.find({defense: {$gt: 70}}).count()
263
```
