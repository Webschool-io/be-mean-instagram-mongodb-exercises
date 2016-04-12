# MongoDB - Aula 05 - Exercício
autor: Nurielly Caroline Brizola


# Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-04-02T13:04:00.096-0300    connected to: 127.0.0.1
2016-04-02T13:04:00.104-0300    dropping: be-mean.restaurantes
2016-04-02T13:04:03.089-0300    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
2016-04-02T13:04:03.936-0300    imported 25359 documents

mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection pokemons --drop --file pokemons.json
2016-04-02T13:13:40.838-0300    connected to: 127.0.0.1
2016-04-02T13:13:40.844-0300    dropping: be-mean-pokemons.pokemons
2016-04-02T13:13:40.943-0300    imported 610 documents
```

# Distinct por cuisine na restaurantes 
```
db.restaurantes.distinct('cuisine')

[
    "Hamburgers",
    "Bakery",
    "American ",
    "Jewish/Kosher",
    "Irish",
    "Delicatessen",
    "Chinese",
    "Ice Cream, Gelato, Yogurt, Ices",
    "Other",
    "Chicken",
    "Turkish",
    "Caribbean",
    "Donuts",
    "Sandwiches/Salads/Mixed Buffet",
    "Continental",
    "Bagels/Pretzels",
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

# Distinct por types na pokemons
```
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

# As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
### Pagina 1
```
{
    "_id" : ObjectId("564b1dad25337263280d0479"),
    "attack" : 56,
    "created" : "2013-11-03T15:05:41.305777",
    "defense" : 35,
    "height" : "3",
    "hp" : 30,
    "name" : "Rattata",
    "speed" : 72,
    "types" : [ 
        "normal"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d047a"),
    "attack" : 52,
    "created" : "2013-11-03T15:05:41.271082",
    "defense" : 43,
    "height" : "6",
    "hp" : 39,
    "name" : "Charmander",
    "speed" : 65,
    "types" : [ 
        "fire"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d047b"),
    "attack" : 64,
    "created" : "2013-11-03T15:05:41.273462",
    "defense" : 58,
    "height" : "11",
    "hp" : 58,
    "name" : "Charmeleon",
    "speed" : 80,
    "types" : [ 
        "fire"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d047d"),
    "attack" : 83,
    "created" : "2013-11-03T15:05:41.282985",
    "defense" : 100,
    "height" : "16",
    "hp" : 79,
    "name" : "Blastoise",
    "speed" : 78,
    "types" : [ 
        "water"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d047c"),
    "attack" : 63,
    "created" : "2013-11-03T15:05:41.280718",
    "defense" : 80,
    "height" : "10",
    "hp" : 59,
    "name" : "Wartortle",
    "speed" : 58,
    "types" : [ 
        "water"
    ]
}
```

### Pagina 2
```
{
    "_id" : ObjectId("564b1dad25337263280d047e"),
    "attack" : 30,
    "created" : "2013-11-03T15:05:41.285736",
    "defense" : 35,
    "height" : "3",
    "hp" : 45,
    "name" : "Caterpie",
    "speed" : 45,
    "types" : [ 
        "bug"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d047f"),
    "attack" : 20,
    "created" : "2013-11-03T15:05:41.288107",
    "defense" : 55,
    "height" : "7",
    "hp" : 50,
    "name" : "Metapod",
    "speed" : 30,
    "types" : [ 
        "bug"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d0480"),
    "attack" : 45,
    "created" : "2013-11-03T15:05:41.290411",
    "defense" : 50,
    "height" : "11",
    "hp" : 60,
    "name" : "Butterfree",
    "speed" : 70,
    "types" : [ 
        "flying", 
        "bug"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d0481"),
    "attack" : 60,
    "created" : "2013-11-03T15:05:41.310402",
    "defense" : 30,
    "height" : "3",
    "hp" : 40,
    "name" : "Spearow",
    "speed" : 70,
    "types" : [ 
        "normal", 
        "flying"
    ]
}
{
    "_id" : ObjectId("564b1dad25337263280d0482"),
    "attack" : 25,
    "created" : "2013-11-03T15:05:41.294947",
    "defense" : 50,
    "height" : "6",
    "hp" : 45,
    "name" : "Kakuna",
    "speed" : 35,
    "types" : [ 
        "poison", 
        "bug"
    ]
}
```

### Pagina 3
```
{
    "_id" : ObjectId("564b1dae25337263280d0483"),
    "attack" : 65,
    "created" : "2013-11-03T15:05:41.439497",
    "defense" : 55,
    "height" : "8",
    "hp" : 52,
    "name" : "Farfetchd",
    "speed" : 60,
    "types" : [ 
        "normal", 
        "flying"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d0485"),
    "attack" : 60,
    "created" : "2013-11-03T15:05:41.437483",
    "defense" : 95,
    "height" : "10",
    "hp" : 50,
    "name" : "Magneton",
    "speed" : 70,
    "types" : [ 
        "steel", 
        "electric"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d0484"),
    "attack" : 35,
    "created" : "2013-11-03T15:05:41.435237",
    "defense" : 70,
    "height" : "3",
    "hp" : 25,
    "name" : "Magnemite",
    "speed" : 45,
    "types" : [ 
        "steel", 
        "electric"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d0486"),
    "attack" : 85,
    "created" : "2013-11-03T15:05:41.441502",
    "defense" : 45,
    "height" : "14",
    "hp" : 35,
    "name" : "Doduo",
    "speed" : 75,
    "types" : [ 
        "normal", 
        "flying"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d0487"),
    "attack" : 45,
    "created" : "2013-11-03T15:05:41.445749",
    "defense" : 55,
    "height" : "11",
    "hp" : 65,
    "name" : "Seel",
    "speed" : 45,
    "types" : [ 
        "water"
    ]
}
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo
### Com group
```
{
    "_id" : "fairy",
    "quantidade" : 28
}
{
    "_id" : "psychic",
    "quantidade" : 62
}
{
    "_id" : "fighting",
    "quantidade" : 38
}
{
    "_id" : "dark",
    "quantidade" : 38
}
{
    "_id" : "ground",
    "quantidade" : 51
}
{
    "_id" : "grass",
    "quantidade" : 75
}
{
    "_id" : "electric",
    "quantidade" : 40
}
{
    "_id" : "steel",
    "quantidade" : 37
}
{
    "_id" : "rock",
    "quantidade" : 46
}
{
    "_id" : "flying",
    "quantidade" : 77
}
{
    "_id" : "fire",
    "quantidade" : 47
}
{
    "_id" : "ice",
    "quantidade" : 24
}
{
    "_id" : "bug",
    "quantidade" : 61
}
{
    "_id" : "poison",
    "quantidade" : 54
}
{
    "_id" : "ghost",
    "quantidade" : 34
}
{
    "_id" : "dragon",
    "quantidade" : 20
}
{
    "_id" : "water",
    "quantidade" : 105
}
{
    "_id" : "normal",
    "quantidade" : 78
}
```

# Realizar 3 counts na pokemons
### Todos
```
db.pokemons.count()

610
```

### Só do tipo fire
```
db.pokemons.count({types: /fire/i })

47
```

### Só dos que tem ataque maior que 70
```
db.pokemons.count({attack: {$gte: 70} }

336
```