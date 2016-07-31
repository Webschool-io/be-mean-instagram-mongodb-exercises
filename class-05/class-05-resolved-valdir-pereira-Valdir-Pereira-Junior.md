## Estrutura


# MongoDB - Aula 05 - Exercício
User: https://github.com/valdir-pereira
Autor: Valdir Pereira Júnior

# Importar as collections `restaurantes` e `pokemons`.

```
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --file pokemons.json
2016-07-29T10:46:45.438-0300    connected to: 127.0.0.1
2016-07-29T10:46:45.690-0300    imported 610 documents

$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --file restaurantes.json
2016-07-29T14:29:46.780-0300    connected to: 127.0.0.1
2016-07-29T14:29:49.637-0300    [###########.............] be-mean.restaurantes 5.4 MB/11.4 MB (47.4%)
2016-07-29T14:29:51.679-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-07-29T14:29:51.680-0300

show collections
pokemons        0.140MB / 0.164MB
restaurantes    14.012MB / 21.465MB
system.indexes  0.000MB / 0.008MB
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.restaurantes.count()
25359
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.count()
610

```
# Distinct por `cuisine` na restaurantes.

```js
db.restaurantes.distinct('cuisine')
[
    "Irish",
    "Bakery",
    "American ",
    "Jewish/Kosher",
    "Delicatessen",
    "Chinese",
    "Ice Cream, Gelato, Yogurt, Ices",
    "Other",
    "Hamburgers",
    "Chicken",
    "Caribbean",
    "Donuts",
    "Turkish",
    "Sandwiches/Salads/Mixed Buffet",
    "Bagels/Pretzels",
    "Pizza",
    "Italian",
    "Steak",
    "Continental",
    "Polish",
    "German",
    "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
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
```

# Distinct por `types` na pokemons.

```js
db.pokemons.distinct('types')
[
    "fire",
    "normal",
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

# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```js
	//Page 1
	Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.find().limit(5).skip(5 * 0)
	{
	    "_id": ObjectId("564b1dad25337263280d047b"),
	    "attack": 64,
	    "created": "2013-11-03T15:05:41.273462",
	    "defense": 58,
	    "height": "11",
	    "hp": 58,
	    "name": "Charmeleon",
	    "speed": 80,
	    "types": [
	        "fire"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d0479"),
	    "attack": 56,
	    "created": "2013-11-03T15:05:41.305777",
	    "defense": 35,
	    "height": "3",
	    "hp": 30,
	    "name": "Rattata",
	    "speed": 72,
	    "types": [
	        "normal"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d047c"),
	    "attack": 63,
	    "created": "2013-11-03T15:05:41.280718",
	    "defense": 80,
	    "height": "10",
	    "hp": 59,
	    "name": "Wartortle",
	    "speed": 58,
	    "types": [
	        "water"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d047e"),
	    "attack": 30,
	    "created": "2013-11-03T15:05:41.285736",
	    "defense": 35,
	    "height": "3",
	    "hp": 45,
	    "name": "Caterpie",
	    "speed": 45,
	    "types": [
	        "bug"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d047d"),
	    "attack": 83,
	    "created": "2013-11-03T15:05:41.282985",
	    "defense": 100,
	    "height": "16",
	    "hp": 79,
	    "name": "Blastoise",
	    "speed": 78,
	    "types": [
	        "water"
	    ]
	}

	//Page 2
	Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.find().limit(5).skip(5 * 1)
	{
	    "_id": ObjectId("564b1dad25337263280d047a"),
	    "attack": 52,
	    "created": "2013-11-03T15:05:41.271082",
	    "defense": 43,
	    "height": "6",
	    "hp": 39,
	    "name": "Charmander",
	    "speed": 65,
	    "types": [
	        "fire"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d0481"),
	    "attack": 60,
	    "created": "2013-11-03T15:05:41.310402",
	    "defense": 30,
	    "height": "3",
	    "hp": 40,
	    "name": "Spearow",
	    "speed": 70,
	    "types": [
	        "normal",
	        "flying"
	    ]
	}
	{
	    "_id": ObjectId("564b1dad25337263280d0482"),
	    "attack": 25,
	    "created": "2013-11-03T15:05:41.294947",
	    "defense": 50,
	    "height": "6",
	    "hp": 45,
	    "name": "Kakuna",
	    "speed": 35,
	    "types": [
	        "poison",
	        "bug"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0483"),
	    "attack": 65,
	    "created": "2013-11-03T15:05:41.439497",
	    "defense": 55,
	    "height": "8",
	    "hp": 52,
	    "name": "Farfetchd",
	    "speed": 60,
	    "types": [
	        "normal",
	        "flying"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0484"),
	    "attack": 35,
	    "created": "2013-11-03T15:05:41.435237",
	    "defense": 70,
	    "height": "3",
	    "hp": 25,
	    "name": "Magnemite",
	    "speed": 45,
	    "types": [
	        "steel",
	        "electric"
	    ]
	}

	//Page 3
	Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.find().limit(5).skip(5 * 2)
	{
	    "_id": ObjectId("564b1dae25337263280d0485"),
	    "attack": 60,
	    "created": "2013-11-03T15:05:41.437483",
	    "defense": 95,
	    "height": "10",
	    "hp": 50,
	    "name": "Magneton",
	    "speed": 70,
	    "types": [
	        "steel",
	        "electric"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0486"),
	    "attack": 85,
	    "created": "2013-11-03T15:05:41.441502",
	    "defense": 45,
	    "height": "14",
	    "hp": 35,
	    "name": "Doduo",
	    "speed": 75,
	    "types": [
	        "normal",
	        "flying"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0487"),
	    "attack": 45,
	    "created": "2013-11-03T15:05:41.445749",
	    "defense": 55,
	    "height": "11",
	    "hp": 65,
	    "name": "Seel",
	    "speed": 45,
	    "types": [
	        "water"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0488"),
	    "attack": 110,
	    "created": "2013-11-03T15:05:41.443720",
	    "defense": 70,
	    "height": "18",
	    "hp": 60,
	    "name": "Dodrio",
	    "speed": 100,
	    "types": [
	        "normal",
	        "flying"
	    ]
	}
	{
	    "_id": ObjectId("564b1dae25337263280d0489"),
	    "attack": 70,
	    "created": "2013-11-03T15:05:41.447897",
	    "defense": 80,
	    "height": "17",
	    "hp": 90,
	    "name": "Dewgong",
	    "speed": 70,
	    "types": [
	        "water",
	        "ice"
	    ]
	}
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo.

```js

db.pokemons.aggregate(
	[
		{ 
			$unwind: '$types' 
		},
		{ $group: {
			_id: '$types',
			total: { $sum: 1 }
			}
		}
	]
);	
{
    "waitedMS": NumberLong("0"),
    "result": [
        {
            "_id": "fire",
            "total": 47
        },
        {
            "_id": "ice",
            "total": 24
        },
        {
            "_id": "dark",
            "total": 38
        },
        {
            "_id": "water",
            "total": 105
        },
        {
            "_id": "normal",
            "total": 78
        },
        {
            "_id": "bug",
            "total": 61
        },
        {
            "_id": "electric",
            "total": 40
        },
        {
            "_id": "poison",
            "total": 54
        },
        {
            "_id": "flying",
            "total": 77
        },
        {
            "_id": "steel",
            "total": 37
        },
        {
            "_id": "ghost",
            "total": 34
        },
        {
            "_id": "fighting",
            "total": 38
        },
        {
            "_id": "psychic",
            "total": 62
        },
        {
            "_id": "fairy",
            "total": 28
        },
        {
            "_id": "grass",
            "total": 75
        },
        {
            "_id": "ground",
            "total": 51
        },
        {
            "_id": "rock",
            "total": 46
        },
        {
            "_id": "dragon",
            "total": 20
        }
    ],
    "ok": 1
}
```

# Realizar 3 counts na pokemons.

```js

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.count({'types' : 'electric'})
40

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.count({'speed': {$gt: 80}})
176

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean> db.pokemons.count({'hp': {$gte: 100}})
71

```

