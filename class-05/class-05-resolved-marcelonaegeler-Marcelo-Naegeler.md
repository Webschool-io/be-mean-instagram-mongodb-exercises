#MongoDB - Aula 05 - Exercícios
Autor: Marcelo André Naegeler

##1. Importar as collections restaurantes (já incluído) e pokémons
```
[marcelo@fedora be-mean-instagram-mongodb-excercises]$ mongoimport --db be-mean-instagram --collection pokemons --drop --file ~/Downloads/pokemons.json
2015-11-23T18:03:52.667-0200  connected to: localhost
2015-11-23T18:03:52.668-0200  dropping: be-mean-instagram.pokemons
2015-11-23T18:03:53.101-0200  imported 610 documents
```

##2. Distinct por `cuisine` na restaurantes
```
> db.restaurantes.distinct( 'cuisine' );
[
  "Hamburgers",
  "Bakery",
  "American ",
  "Irish",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Donuts",
  "Caribbean",
  "Bagels/Pretzels",
  "Sandwiches/Salads/Mixed Buffet",
  "Turkish",
  "Continental",
  "Pizza",
  "Italian",
  "Steak",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Polish",
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
  "African",
  "Not Listed/Not Applicable",
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

##3. Distinct por `types` na pokémons
```
> db.pokemons.distinct( 'types' );
[
  "fire",
  "water",
  "bug",
  "flying",
  "normal",
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

##4. As primeiras 3 pág. com .limit() e .skip() de pokémons (5 em 5)
```
> db.pokemons.find( {}, { name: 1, _id: 0 } ).limit( 5 ).skip( 5 * 0 )
{ "name" : "Charmeleon" }
{ "name" : "Wartortle" }
{ "name" : "Blastoise" }
{ "name" : "Caterpie" }
{ "name" : "Metapod" }

> db.pokemons.find( {}, { name: 1, _id: 0 } ).limit( 5 ).skip( 5 * 1 )
{ "name" : "Charmander" }
{ "name" : "Butterfree" }
{ "name" : "Rattata" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

> db.pokemons.find( {}, { name: 1, _id: 0 } ).limit( 5 ).skip( 5 * 2 )
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
```

##5. Group ou Aggregate contando a quantidade de pokémons de cada tipo
```
> db.pokemons.aggregate( [
	{ $unwind: '$types' }
  , {
  	$group: {
			_id: '$types'
		  , total: { $sum: 1 }
		}
	}
] );
{ "_id" : "fairy", "total" : 28 }
{ "_id" : "psychic", "total" : 62 }
{ "_id" : "fighting", "total" : 38 }
{ "_id" : "dark", "total" : 38 }
{ "_id" : "ground", "total" : 51 }
{ "_id" : "grass", "total" : 75 }
{ "_id" : "electric", "total" : 40 }
{ "_id" : "steel", "total" : 37 }
{ "_id" : "rock", "total" : 46 }
{ "_id" : "flying", "total" : 77 }
{ "_id" : "fire", "total" : 47 }
{ "_id" : "ice", "total" : 24 }
{ "_id" : "bug", "total" : 61 }
{ "_id" : "poison", "total" : 54 }
{ "_id" : "normal", "total" : 78 }
{ "_id" : "ghost", "total" : 34 }
{ "_id" : "dragon", "total" : 20 }
{ "_id" : "water", "total" : 105 }
```

##6. Realizar 3 counts na pokémons.

* Todos:
```
> db.pokemons.count();
610
```

* Só do `types` `water`:
```
> db.pokemons.count( { types: "water" } );
105
```

* Só com ataque maior que 60:
```
> db.pokemons.count( { attack: { $gt: 60 } } );
390
```
