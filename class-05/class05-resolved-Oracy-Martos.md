# MongoDB - Aula 05 - Exercício
Autor: Oracy Martos

Be-mean

# 1- Importar as collections Restaurantes e Pokemons
```
oracy@oracy-X555UB:~/Documentos/bemean/MongoDb-ebook/src/data! mongoimport --db pokemons --host=127.0.0.1 --drop --file pokemons.json
2017-03-06T19:12:33.505-0300    no collection specified
2017-03-06T19:12:33.505-0300    using filename 'pokemons' as collection
2017-03-06T19:12:33.505-0300    connected to: 127.0.0.1
2017-03-06T19:12:33.506-0300    dropping: pokemons.pokemons
2017-03-06T19:12:33.544-0300    imported 610 documents
oracy@oracy-X555UB:~/Documentos/bemean/MongoDb-ebook/src/data! mongoimport --db restaurantes --host=127.0.0.1 --drop --file restaurantes.json
2017-03-06T19:12:41.321-0300    no collection specified
2017-03-06T19:12:41.321-0300    using filename 'restaurantes' as collection
2017-03-06T19:12:41.322-0300    connected to: 127.0.0.1
2017-03-06T19:12:41.322-0300    dropping: restaurantes.restaurantes
2017-03-06T19:12:42.314-0300    imported 25359 documents
```

# 2- Distinct por `cuisine` na restaurantes
```
> db.restaurantes.distinct('cuisine')
[
    "American ",
    "Irish",
    "Jewish/Kosher",
    "Hamburgers",
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
    "Bakery",
    "Pizza",
    "Italian",
    "Steak",
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

# 3- Distinct por `types` na pokemons
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
    "ice",
    "ghost",
    "psychic",
    "fighting",
    "grass",
    "ground",
    "fairy",
    "rock",
    "dark",
    "dragon"
]
```

# 4- As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
> db.pokemons.find().limit(5).skip(5*0).pretty()
{
 ---   "_id" : ObjectId("564b1dad25337263280d0479"),
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

> db.pokemons.find().limit(5).skip(5*1).pretty()
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

> db.pokemons.find().limit(5).skip(5*2).pretty()
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
```

# 5- Group ou Aggregate contando a quantidade de pokemons de cada Type
```
db.pokemons.aggregate([
  { $unwind : "$types"},
  { $group: {
    _id: "$types",
    total: {$sum: 1}
    }
  }
])
{ "_id" : "fairy", "total" : 28 }
{ "_id" : "fighting", "total" : 38 }
{ "_id" : "psychic", "total" : 62 }
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
{ "_id" : "ghost", "total" : 34 }
{ "_id" : "dragon", "total" : 20 }
{ "_id" : "water", "total" : 105 }
{ "_id" : "normal", "total" : 78 }
```

# 6- Realizar 3 counts na pokemons.
```
> db.pokemons.count()
610
> db.pokemons.count({types: "fire"})
47
> db.pokemons.count({defense: {$gt: 70}})
250
```