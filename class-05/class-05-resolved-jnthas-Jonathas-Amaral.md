# MongoDB - Aula 05 - Exercicio
autor: Jonathas Amaral

## 1. Importar as collections restaurantes e pokemons
```
// Restaurantes
Jnthss-MacBook:~ jonathas$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json 
2015-11-21T21:05:03.170-0200    connected to: 127.0.0.1
2015-11-21T21:05:03.170-0200    dropping: be-mean.restaurantes
2015-11-21T21:05:04.934-0200    imported 25359 documents

// Pokemons
Jnthss-MacBook:~ jonathas$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Downloads/pokemons.json 
2015-11-21T20:58:11.545-0200    connected to: 127.0.0.1
2015-11-21T20:58:11.546-0200    dropping: be-mean.pokemons
2015-11-21T20:58:11.746-0200    imported 610 documents
```


## 2. Distinct por `cuisine` na restaurantes
```
> db.restaurantes.distinct('cuisine');
[
    "American ",
    "Irish",
    "Hamburgers",
    "Bakery",
    "Jewish/Kosher",
    "Ice Cream, Gelato, Yogurt, Ices",
    "Delicatessen",
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

## 3. Distinct por `types` na pokemons
```
> db.pokemons.distinct('types');
[
    "normal",
    "water",
    "bug",
    "flying",
    "fire",
    "poison",
    "electric",
    "steel",
    "ghost",
    "ice",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
// Pagina 1
db.pokemons.find().limit(5).skip(5 * 0);
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
Fetched 5 record(s) in 6ms

// Pagina 2
db.pokemons.find().limit(5).skip(5 * 1);
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
Fetched 5 record(s) in 5ms

// Pagina 3
db.pokemons.find().limit(5).skip(5 * 2);
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
Fetched 5 record(s) in 5ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
db.pokemons.aggregate([
  {$unwind: '$types'},
  {$group: {_id: '$types', total: {$sum: 1}}}
])
```
Resultado:
```
Jnthss-MacBook(mongod-3.0.7) be-mean> db.pokemons.aggregate([   {$unwind: '$types'},   {$group: {_id: '$types', total: {$sum: 1}}} ])
{
  "result": [
    {
      "_id": "fairy",
      "total": 28
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
      "_id": "dark",
      "total": 38
    },
    {
      "_id": "ground",
      "total": 51
    },
    {
      "_id": "grass",
      "total": 75
    },
    {
      "_id": "electric",
      "total": 40
    },
    {
      "_id": "steel",
      "total": 37
    },
    {
      "_id": "rock",
      "total": 46
    },
    {
      "_id": "flying",
      "total": 77
    },
    {
      "_id": "fire",
      "total": 47
    },
    {
      "_id": "ice",
      "total": 24
    },
    {
      "_id": "bug",
      "total": 61
    },
    {
      "_id": "poison",
      "total": 54
    },
    {
      "_id": "ghost",
      "total": 34
    },
    {
      "_id": "dragon",
      "total": 20
    },
    {
      "_id": "water",
      "total": 105
    },
    {
      "_id": "normal",
      "total": 78
    }
  ],
  "ok": 1
}
```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
```
Jnthss-MacBook(mongod-3.0.7) be-mean> db.pokemons.count({})
610
```

-> .count -- só tipo fogo
```
Jnthss-MacBook(mongod-3.0.7) be-mean> db.pokemons.count({types: {$in: ['fire']}})
47
```

-> .count -- só de quantos tem a defesa maior que 70
```
Jnthss-MacBook(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```






