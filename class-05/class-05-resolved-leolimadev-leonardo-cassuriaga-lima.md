# MongoDB - Aula 05 - Exercício

autor: Leonardo Cassuriaga Lima

##1. Importar as collections restaurantes e pokemons.

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json  
2015-11-22T17:20:49.273-0200    connected to: localhost  
2015-11-22T17:20:49.276-0200    dropping: be-mean.restaurantes  
2015-11-22T17:20:50.853-0200    imported 25359 documents  

mongoimport --db be-mean --collection  pokemons --drop --file pokemons.json  
2015-11-22T17:22:00.585-0200    connected to: localhost  
2015-11-22T17:22:00.587-0200    dropping: be-mean. pokemons  
2015-11-22T17:22:00.633-0200    imported 610 documents  


##2. Distinct por 'cuisine' na restaurantes.

> db.restaurantes.distinct('cuisine')  
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
        "Italian",  
        "Steak",  
        "Polish",  
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",  
        "German",  
        "French",  
        "Pizza",  
        "Pizza/Italian",  
        "Mexican",  
        "Spanish",  
        "Café/Coffee/Tea",  
        "Pancakes/Waffles",  
        "Tex-Mex",  
        "Soul Food",  
        "Seafood",  
        "Greek",  
        "Hotdogs",  
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

##3. Distinct por 'types' na pokemons.

> db.pokemons.distinct('types')  
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

##4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5).

*Primeira página*

> db.pokemons.find().limit(5).skip(5 * 0)  
{  
    "_id": ObjectId("564b1dad25337263280d047a"),  
    "attack": 52,  
    "created": "2013-11-03T15:05:41.271082",  
    "defense": 43,  
    "height": "6",  
    "hp": 39,  
    "name": "Charmander",  
    "speed": 65,  
    "types": ["fire"]  
} {  
    "_id": ObjectId("564b1dad25337263280d047c"),  
    "attack": 63,  
    "created": "2013-11-03T15:05:41.280718",  
    "defense": 80,  
    "height": "10",  
    "hp": 59,  
    "name": "Wartortle",  
    "speed": 58,  
    "types": ["water"]  
} {  
    "_id": ObjectId("564b1dad25337263280d047d"),  
    "attack": 83,  
    "created": "2013-11-03T15:05:41.282985",  
    "defense": 100,  
    "height": "16",  
    "hp": 79,  
    "name": "Blastoise",  
    "speed": 78,  
    "types": ["water"]  
} {  
    "_id": ObjectId("564b1dad25337263280d047b"),  
    "attack": 64,  
    "created": "2013-11-03T15:05:41.273462",  
    "defense": 58,  
    "height": "11",  
    "hp": 58,  
    "name": "Charmeleon",  
    "speed": 80,  
    "types": ["fire"]  
} {  
    "_id": ObjectId("564b1dad25337263280d047e"),  
    "attack": 30,  
    "created": "2013-11-03T15:05:41.285736",  
    "defense": 35,  
    "height": "3",  
    "hp": 45,  
    "name": "Caterpie",  
    "speed": 45,  
    "types": ["bug"]  
}  

*Segunda página*

> db.pokemons.find().limit(5).skip(5 * 1)  
{  
    "_id": ObjectId("564b1dad25337263280d047f"),  
    "attack": 20,  
    "created": "2013-11-03T15:05:41.288107",  
    "defense": 55,  
    "height": "7",  
    "hp": 50,  
    "name": "Metapod",  
    "speed": 30,  
    "types": ["bug"]  
} {  
    "_id": ObjectId("564b1dad25337263280d0480"),  
    "attack": 45,  
    "created": "2013-11-03T15:05:41.290411",  
    "defense": 50,  
    "height": "11",  
    "hp": 60,  
    "name": "Butterfree",  
    "speed": 70,  
    "types": ["flying", "bug"]  
} {  
    "_id": ObjectId("564b1dad25337263280d0481"),  
    "attack": 60,  
    "created": "2013-11-03T15:05:41.310402",  
    "defense": 30,  
    "height": "3",  
    "hp": 40,  
    "name": "Spearow",  
    "speed": 70,  
    "types": ["normal", "flying"]  
} {  
    "_id": ObjectId("564b1dad25337263280d0482"),  
    "attack": 25,  
    "created": "2013-11-03T15:05:41.294947",  
    "defense": 50,  
    "height": "6",  
    "hp": 45,  
    "name": "Kakuna",  
    "speed": 35,  
    "types": ["poison", "bug"]  
} {  
    "_id": ObjectId("564b1dae25337263280d0483"),  
    "attack": 65,  
    "created": "2013-11-03T15:05:41.439497",  
    "defense": 55,  
    "height": "8",  
    "hp": 52,  
    "name": "Farfetchd",  
    "speed": 60,  
    "types": ["normal", "flying"]  
}  

*Terceira página*

> db.pokemons.find().limit(5).skip(5 * 2)  
{  
    "_id": ObjectId("564b1dae25337263280d0484"),  
    "attack": 35,  
    "created": "2013-11-03T15:05:41.435237",  
    "defense": 70,  
    "height": "3",  
    "hp": 25,  
    "name": "Magnemite",  
    "speed": 45,  
    "types": ["steel", "electric"]  
} {  
    "_id": ObjectId("564b1dae25337263280d0485"),  
    "attack": 60,  
    "created": "2013-11-03T15:05:41.437483",  
    "defense": 95,  
    "height": "10",  
    "hp": 50,  
    "name": "Magneton",  
    "speed": 70,  
    "types": ["steel", "electric"]  
} {  
    "_id": ObjectId("564b1dae25337263280d0486"),  
    "attack": 85,  
    "created": "2013-11-03T15:05:41.441502",  
    "defense": 45,  
    "height": "14",  
    "hp": 35,  
    "name": "Doduo",  
    "speed": 75,  
    "types": ["normal", "flying"]  
} {  
    "_id": ObjectId("564b1dae25337263280d0487"),  
    "attack": 45,  
    "created": "2013-11-03T15:05:41.445749",  
    "defense": 55,  
    "height": "11",  
    "hp": 65,  
    "name": "Seel",  
    "speed": 45,  
    "types": ["water"]  
} {  
    "_id": ObjectId("564b1dae25337263280d0488"),  
    "attack": 110,  
    "created": "2013-11-03T15:05:41.443720",  
    "defense": 70,  
    "height": "18",  
    "hp": 60,  
    "name": "Dodrio",  
    "speed": 100,  
    "types": ["normal", "flying"]  
}  

##5. Group ou Aggregate contando a quantidade de pokemons de cada tipo.

db.pokemons.aggregate([  
	{$unwind: '$types'},  
	{$group:{_id:'$types', count: {$sum : 1}}},  
	{$project:{tmp:{Tipo:'$_id', quantidade:'$count' }}},  
	{$group: {_id: null, total: { $sum: '$tmp.quantidade' }, data: {$addToSet: '$tmp'}}}  
])  

{  
    "_id": null,  
    "total": 915,  
    "data": [{  
        "Tipo": "water",  
        "quantidade": 105  
    }, {  
        "Tipo": "normal",  
        "quantidade": 78  
    }, {  
        "Tipo": "flying",  
        "quantidade": 77  
    }, {  
        "Tipo": "psychic",  
        "quantidade": 62  
    }, {  
        "Tipo": "fire",  
        "quantidade": 47  
    }, {  
        "Tipo": "grass",  
        "quantidade": 75  
    }, {  
        "Tipo": "ice",  
        "quantidade": 24  
    }, {  
        "Tipo": "fighting",  
        "quantidade": 38  
    }, {  
        "Tipo": "steel",  
        "quantidade": 37  
    }, {  
        "Tipo": "ground",  
        "quantidade": 51  
    }, {  
        "Tipo": "ghost",  
        "quantidade": 34  
    }, {  
        "Tipo": "dark",  
        "quantidade": 38  
    }, {  
        "Tipo": "rock",  
        "quantidade": 46  
    }, {  
        "Tipo": "electric",  
        "quantidade": 40  
    }, {  
        "Tipo": "dragon",  
        "quantidade": 20  
    }, {  
        "Tipo": "fairy",  
        "quantidade": 28  
    }, {  
        "Tipo": "bug",  
        "quantidade": 61  
    }, {  
        "Tipo": "poison",  
        "quantidade": 54  
    }]  
}  

##6. Realizar 3 counts na pokemons.

> db.pokemons.count()  
610  
> db.pokemons.count({ types: 'fire'})  
47  
> db.pokemons.count({ defense: { $gt: 70}})  
250  