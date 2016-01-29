1. Importar as collections restaurantes e pokemons.json;
2. Distinct por cuisine na restaurantes;
3. Distinct por types na pokemons;
4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
5. Um group ou aggregate contando a quantidade de pokemons de cada tipo
6. Realizar 3 counts na pokemons.
	
	.count -- todos
	.count -- só tipo fogo
	.count -- só de quantos tem a defesa maior que 70


1. Importar as collections restaurantes e pokemons.json;

```

	mongoimport --host 127.0.0.1 --db be-mean-instagram --collection pokemons --drop --file ~/Desktop/be-mean-instagram-mongodb/exercises/pokemons.json 
	2015-12-24T21:42:14.235-0200	connected to: 127.0.0.1
	2015-12-24T21:42:14.236-0200	dropping: be-mean-instagram.pokemons
	2015-12-24T21:42:14.255-0200	imported 620 documents

	mongoimport --host 127.0.0.1 --db be-mean-instagram --collection restaurantes --drop --file ~/Desktop/be-mean-instagram-mongodb/exercises/restaurantes.json 
	2015-12-24T21:38:43.860-0200	connected to: 127.0.0.1
	2015-12-24T21:38:43.861-0200	dropping: be-mean-instagram.restaurantes
	2015-12-24T21:38:45.250-0200	imported 25359 documents


```

2. Distinct por cuisine na restaurantes;

```

	 db.restaurantes.distinct('cuisine')

	[
	  "American ",
	  "Irish",
	  "Hamburgers",
	  "Bakery",
	  "Jewish/Kosher",
	  "Delicatessen",
	  "Ice Cream, Gelato, Yogurt, Ices",
	  "Chinese",
	  "Other",
	  "Chicken",
	  "Caribbean",
	  "Turkish",
	  "Donuts",
	  "Sandwiches/Salads/Mixed Buffet",
	  "Bagels/Pretzels",
	  "Continental",
	  "Pizza",
	  "Italian",
	  "Steak",
	  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
	  "Polish",
	  "German",
	  "Pizza/Italian",
	  "French",
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

3. Distinct por types na pokemons;

```

	be-mean-instagram> db.pokemons.distinct('types').sort()
	
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

4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```

	be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
	{
	  "name": "Pidgeotto"
	}
	{
	  "name": "Beedrill"
	}
	{
	  "name": "Pidgey"
	}
	{
	  "name": "Raticate"
	}
	{
	  "name": "Pikachu"
	}
	
	Fetched 5 record(s) in 1ms
	
	be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
	{
	  "name": "Fearow"
	}
	{
	  "name": "Ekans"
	}
	{
	  "name": "Raichu"
	}
	{
	  "name": "Poliwag"
	}
	{
	  "name": "Arbok"
	}
	
	Fetched 5 record(s) in 1ms
	
	be-mean-instagram> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
	{
	  "name": "Poliwrath"
	}
	{
	  "name": "Poliwhirl"
	}
	{
	  "name": "Abra"
	}
	{
	  "name": "Kadabra"
	}
	{
	  "name": "Machop"
	}

	Fetched 5 record(s) in 1ms

```

5. Um group ou aggregate contando a quantidade de pokemons de cada tipo

```
	
	 db.pokemons.group({
	 	initial: {total: 0},
	 		reduce: function(curr , result) {
	 			curr.types.forEach(function(type) {
	 				if(result[type]) {
	 					result[type] += 1;
	 				} else {
	 				result[type] = 1;
	 			}
	 			result.total += 1;
				});
	 		}
	 	});

	[
	  {
	    "total": 934,
	    "normal": 79,
	    "flying": 81,
	    "poison": 54,
	    "bug": 58,
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

6. Realizar 3 counts na pokemons.
	
	.count -- todos
	.count -- só tipo fogo
	.count -- só de quantos tem a defesa maior que 70


```
	
	db.pokemons.count()
	620
	
	db.pokemons.count({types: 'fire'})
	53
	
	db.pokemons.count({defense: {$gt : 70}})
	263

```