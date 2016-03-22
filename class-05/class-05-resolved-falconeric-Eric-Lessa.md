# MongoDB - Aula 05 - Exercício
User: [falconeric](https://github.com/falconeric)
Autor: Eric Lessa

# Importar as collections `restaurantes` e `pokemons`.
```
elcarvalho:~ ericlessa$ mongoimport --db be-mean-instagram --collection restaurantes --drop --file ~/Desktop/BeMEAN/be-mean-modulo-mongodb/material/restaurantes.json
2016-03-19T11:50:21.022-0300	connected to: localhost
2016-03-19T11:50:21.022-0300	dropping: be-mean-instagram.restaurantes
2016-03-19T11:50:22.330-0300	imported 25359 documents
```

```
elcarvalho:~ ericlessa$ mongoimport --db be-mean-pokemons --collection pokemons --drop --file ~/Desktop/BeMEAN/be-mean-modulo-mongodb/material/pokemons.json
2016-03-19T11:48:19.810-0300	connected to: localhost
2016-03-19T11:48:19.811-0300	dropping: be-mean-pokemons.pokemons
2016-03-19T11:48:19.887-0300	imported 610 documents
```

# Distinct por `cuisine` na restaurantes.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.distinct("cuisine")
[
  "American ",
  "Hamburgers",
  "Jewish/Kosher",
  "Irish",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Delicatessen",
  "Bakery",
  "Chicken",
  "Caribbean",
  "Donuts",
  "Turkish",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
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
```
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.distinct("types")
[
  "water",
  "bug",
  "fire",
  "flying",
  "normal",
  "electric",
  "steel",
  "ice",
  "poison",
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
```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var qtd = 5
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find().limit(qtd).skip(qtd * 0)
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
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ]
}
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
Fetched 5 record(s) in 6ms

elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find().limit(qtd).skip(qtd * 1)
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
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
Fetched 5 record(s) in 6ms

elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find().limit(qtd).skip(qtd * 2)
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
Fetched 5 record(s) in 6ms
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.aggregate([
...   {$unwind : '$types'},
...   {
...     $group : {
...       _id : '$types',
...       qty : {$sum : 1}
...     }
...   }
... ])
{
  "waitedMS": NumberLong("0"),
  "result": [
    {
      "_id": "grass",
      "qty": 75
    },
    {
      "_id": "dark",
      "qty": 38
    },
    {
      "_id": "fairy",
      "qty": 28
    },
    {
      "_id": "psychic",
      "qty": 62
    },
    {
      "_id": "ground",
      "qty": 51
    },
    {
      "_id": "poison",
      "qty": 54
    },
    {
      "_id": "ice",
      "qty": 24
    },
    {
      "_id": "electric",
      "qty": 40
    },
    {
      "_id": "dragon",
      "qty": 20
    },
    {
      "_id": "bug",
      "qty": 61
    },
    {
      "_id": "steel",
      "qty": 37
    },
    {
      "_id": "fighting",
      "qty": 38
    },
    {
      "_id": "normal",
      "qty": 78
    },
    {
      "_id": "flying",
      "qty": 77
    },
    {
      "_id": "fire",
      "qty": 47
    },
    {
      "_id": "ghost",
      "qty": 34
    },
    {
      "_id": "rock",
      "qty": 46
    },
    {
      "_id": "water",
      "qty": 105
    }
  ],
  "ok": 1
}
```

# Realizar 3 counts na pokemons.
```
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.count()
610

elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.count({types:'fire'})
47

elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.count({defense:{$gt:70}})
250
```
