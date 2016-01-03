# MongoDB - Aula 05 - Exercício
autor: Vagner Pereira Silva

## Importar as collections restaurantes e pokemons

```
F:\>mongoimport /host:127.0.0.1 /db:be-mean /collection:pokemons /drop /file:CursoMongoDB\pokemons.json
2016-01-03T03:13:22.757-0200    connected to: 127.0.0.1
2016-01-03T03:13:22.776-0200    dropping: be-mean.pokemons
2016-01-03T03:13:22.843-0200    imported 620 documents


F:\>mongoimport /h 127.0.0.1 /d be-mean /c restaurantes /file: CursoMongoDB\restaurantes.json /drop
2016-01-03T03:16:00.202-0200    connected to: 127.0.0.1
2016-01-03T03:16:00.207-0200    dropping: be-mean.restaurantes
2016-01-03T03:16:01.463-0200    imported 25359 documents

```

## Fazer um distinct por `cuisine` na collection restaurantes
```js
connecting to: be-mean
> db.restaurantes.distinct('cuisine')
[
        "Bakery",
        "Jewish/Kosher",
        "American ",
        "Hamburgers",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Other",
        "Chicken",
        "Donuts",
        "Turkish",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Pizza",
        "Caribbean",
        "Irish",
        "Italian",
        "Steak",
        "Continental",
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
        "Greek",
        "Not Listed/Not Applicable",
        "African",
        "Hotdogs",
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
>

```

## Fazer um distinct por `types` na collection pokemons

```js
> db.pokemons.distinct('types')
[
        "normal",
        "bug",
        "poison",
        "flying",
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)

```js

> db.pokemons.find().limit(5).skip(5*0)
{ "_id" : ObjectId("564a7c362c153ed825a69058"), "attack" : 81, "created" : "2013-11-03T15:05:41.308092", "defense" : 60, "height" : "7", "hp" : 55, "name" : "Raticate", "speed" : 97, "types" : [ "normal" ] }
{ "_id" : ObjectId("564a7c362c153ed825a69054"), "attack" : 90, "created" : "2013-11-03T15:05:41.297180", "defense" : 40, "height" : "10", "hp" : 65, "name" : "Beedrill", "speed" : 75, "types" : [ "poison", "bug" ] }
{ "_id" : ObjectId("564a7c362c153ed825a69055"), "attack" : 45, "created" : "2013-11-03T15:05:41.299457", "defense" : 40, "height" : "3", "hp" : 40, "name" : "Pidgey", "speed" : 56, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905b"), "attack" : 60, "created" : "2013-11-03T15:05:41.313816", "defense" : 44, "height" : "20", "hp" : 35, "name" : "Ekans", "speed" : 55, "types" : [ "poison" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905a"), "attack" : 55, "created" : "2013-11-03T15:05:41.317235", "defense" : 40, "height" : "4", "hp" : 35, "name" : "Pikachu", "speed" : 90, "types" : [ "electric" ] }

> db.pokemons.find().limit(5).skip(5*1)
{ "_id" : ObjectId("564a7c362c153ed825a69057"), "attack" : 80, "created" : "2013-11-03T15:05:41.303569", "defense" : 75, "height" : "15", "hp" : 83, "name" : "Pidgeot", "speed" : 101, "types" : [ "normal", "flying" ]}
{ "_id" : ObjectId("564a7c362c153ed825a6905c"), "attack" : 90, "created" : "2013-11-03T15:05:41.318944", "defense" : 55, "height" : "8", "hp" : 60, "name" : "Raichu", "speed" : 110, "types" : [ "electric" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905d"), "attack" : 85, "created" : "2013-11-03T15:05:41.315504", "defense" : 69, "height" : "35", "hp" : 60, "name" : "Arbok", "speed" : 80, "types" : [ "poison" ] }
{ "_id" : ObjectId("564a7c372c153ed825a6905e"), "attack" : 50, "created" : "2013-11-03T15:05:41.388462", "defense" : 40, "height" : "6", "hp" : 40, "name" : "Poliwag", "speed" : 90, "types" : [ "water" ] }
{ "_id" : ObjectId("564a7c372c153ed825a6905f"), "attack" : 65, "created" : "2013-11-03T15:05:41.390744", "defense" : 65, "height" : "10", "hp" : 65, "name" : "Poliwhirl", "speed" : 90, "types" : [ "water" ] }

> db.pokemons.find().limit(5).skip(5*2)
{ "_id" : ObjectId("564a7c372c153ed825a69060"), "attack" : 95, "created" : "2013-11-03T15:05:41.393388", "defense" : 95, "height" : "13", "hp" : 90, "name" : "Poliwrath", "speed" : 70, "types" : [ "fighting", "water"] }
{ "_id" : ObjectId("564a7c372c153ed825a69062"), "attack" : 35, "created" : "2013-11-03T15:05:41.398045", "defense" : 30, "height" : "13", "hp" : 40, "name" : "Kadabra", "speed" : 105, "types" : [ "psychic" ] }
{ "_id" : ObjectId("564a7c372c153ed825a69063"), "attack" : 80, "created" : "2013-11-03T15:05:41.402119", "defense" : 50, "height" : "8", "hp" : 70, "name" : "Machop", "speed" : 35, "types" : [ "fighting" ] }
{ "_id" : ObjectId("564a7c372c153ed825a69061"), "attack" : 20, "created" : "2013-11-03T15:05:41.396006", "defense" : 15, "height" : "9", "hp" : 25, "name" : "Abra", "speed" : 90, "types" : [ "psychic" ] }
{ "_id" : ObjectId("564a7c372c153ed825a69064"), "attack" : 100, "created" : "2013-11-03T15:05:41.404294", "defense" : 70, "height" : "15", "hp" : 80, "name" : "Machoke", "speed" : 45, "types" : [ "fighting" ] }


```

## Apresentar quantidade de pokemons de cada `type` (group ou aggregate)

```js
db.pokemons.aggregate([
	{
		$project: {types:1, _id:0}
	},
	{
		$unwind: '$types'
	},
	{
		$group:{
			_id:'$types',
			qnt: {$sum: 1}
		}
	}

	]);
	
{ "_id" : "dark", "qnt" : 35 }
{ "_id" : "water", "qnt" : 101 }
{ "_id" : "normal", "qnt" : 79 }
{ "_id" : "fairy", "qnt" : 31 }
{ "_id" : "grass", "qnt" : 70 }
{ "_id" : "electric", "qnt" : 47 }
{ "_id" : "flying", "qnt" : 81 }
{ "_id" : "poison", "qnt" : 54 }
{ "_id" : "bug", "qnt" : 58 }
{ "_id" : "psychic", "qnt" : 61 }
{ "_id" : "fighting", "qnt" : 42 }
{ "_id" : "fire", "qnt" : 53 }
{ "_id" : "rock", "qnt" : 42 }
{ "_id" : "ice", "qnt" : 28 }
{ "_id" : "ground", "qnt" : 53 }
{ "_id" : "steel", "qnt" : 35 }
{ "_id" : "ghost", "qnt" : 34 }
{ "_id" : "dragon", "qnt" : 30 }


```

## Realizar 3 counts na pokemons.

```js

> db.pokemons.count({'types':'water'})
101
> db.pokemons.count({'types':'fire'})
53
> db.pokemons.count()
620
>

```
