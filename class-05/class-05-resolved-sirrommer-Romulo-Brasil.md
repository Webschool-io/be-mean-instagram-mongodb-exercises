# MongoDB - Aula 05 - Exercício
autor: sirrommer - Rômulo Brasil

## Importar as collections restaurantes e pokemons
```
new-host-3:data RomuloBrasil$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-08T13:55:34.310-0300	connected to: 127.0.0.1
2015-12-08T13:55:34.310-0300	dropping: be-mean.restaurantes
2015-12-08T13:55:35.755-0300	imported 25359 documents

new-host-3:data RomuloBrasil$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemon.json
2015-12-08T13:56:40.582-0300	connected to: 127.0.0.1
2015-12-08T13:56:40.582-0300	dropping: be-mean.pokemons
2015-12-08T13:56:40.633-0300	imported 610 documents
```

## Fazer um distinct por `cuisine` na collection restaurantes
```
> db.restaurantes.distinct('cuisine')
[
    "Bakery",
    "American ",
    "Irish",
    "Hamburgers",
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

## Fazer um distinct por `types` na collection pokemons
```
> db.pokemons.distinct('types')
[
    "normal",
    "fire",
    "water",
    "bug",
    "flying",
    "poison",
    "electric",
    "steel",
    "ghost",
    "ice",
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)
```
> db.pokemons.find().limit(5).skip(5 * 0).pretty()
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

> db.pokemons.find().limit(5).skip(5 * 1).pretty()
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

> db.pokemons.find().limit(5).skip(5 * 3).pretty()
{
    "_id" : ObjectId("564b1dae25337263280d0488"),
    "attack" : 110,
    "created" : "2013-11-03T15:05:41.443720",
    "defense" : 70,
    "height" : "18",
    "hp" : 60,
    "name" : "Dodrio",
    "speed" : 100,
    "types" : [
        "normal",
        "flying"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d048a"),
    "attack" : 35,
    "created" : "2013-11-03T15:05:41.457865",
    "defense" : 30,
    "height" : "13",
    "hp" : 30,
    "name" : "Gastly",
    "speed" : 80,
    "types" : [
        "poison",
        "ghost"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d0489"),
    "attack" : 70,
    "created" : "2013-11-03T15:05:41.447897",
    "defense" : 80,
    "height" : "17",
    "hp" : 90,
    "name" : "Dewgong",
    "speed" : 70,
    "types" : [
        "water",
        "ice"
    ]
}
{
    "_id" : ObjectId("564b1dae25337263280d048b"),
    "attack" : 95,
    "created" : "2013-11-03T15:05:41.456387",
    "defense" : 180,
    "height" : "15",
    "hp" : 50,
    "name" : "Cloyster",
    "speed" : 70,
    "types" : [
        "water",
        "ice"
    ]
}
{
    "_id" : ObjectId("564b1daf25337263280d048d"),
    "attack" : 50,
    "created" : "2013-11-03T15:05:41.388462",
    "defense" : 40,
    "height" : "6",
    "hp" : 40,
    "name" : "Poliwag",
    "speed" : 90,
    "types" : [
        "water"
    ]
}
```

## Realizar 3 counts na pokemons.

1. count -- todos
```
> db.pokemons.count()
610
```

2. count -- só tipo fogo
```
> db.pokemons.count({types: 'fire'})
47
```

3. count -- só de quantos tem a defesa maior que 70
```
> db.pokemons.count({defense: {$gt:70}})
250
```