# MongoDB - Aula 05 - Exercício
autor: Dayvson Sales

## 1. Importar as collections restaurantes e pokemons
```js
mongoimport --drop --file pokemons.json --collection pokemons --db be-mean-pokemons
connected to: 127.0.0.1
Thu Nov 19 08:53:09.572 dropping: be-mean-pokemons.pokemons
Thu Nov 19 08:53:09.626 check 9 620
Thu Nov 19 08:53:09.628 imported 620 objects

mongoimport --drop --file restaurantes.json --collection restaurantes --db be-mean-pokemons
connected to: 127.0.0.1
Thu Nov 19 08:54:19.562 dropping: be-mean-pokemons.restaurantes
Thu Nov 19 08:54:19.616 check 9 25359
Thu Nov 19 08:54:19.638 imported 25359 objects
```


## 2. Distinct por `cuisine` na restaurantes
```js
dayvs0n-notebook(mongod-2.4.9) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
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

## 3. Distinct por `types` na pokemons
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.distinct('types')
[
  "bug",
  "poison",
  "flying",
  "normal",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```js
// Página 1
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find().limit(5).skip(5*0)
{
  "_id": ObjectId("564a7c362c153ed825a69054"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.297180",
  "defense": 40,
  "height": "10",
  "hp": 65,
  "name": "Beedrill",
  "speed": 75,
  "types": [
    "poison",
    "bug"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69055"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.299457",
  "defense": 40,
  "height": "3",
  "hp": 40,
  "name": "Pidgey",
  "speed": 56,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69056"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.301609",
  "defense": 55,
  "height": "11",
  "hp": 63,
  "name": "Pidgeotto",
  "speed": 71,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69057"),
  "attack": 80,
  "created": "2013-11-03T15:05:41.303569",
  "defense": 75,
  "height": "15",
  "hp": 83,
  "name": "Pidgeot",
  "speed": 101,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69058"),
  "attack": 81,
  "created": "2013-11-03T15:05:41.308092",
  "defense": 60,
  "height": "7",
  "hp": 55,
  "name": "Raticate",
  "speed": 97,
  "types": [
    "normal"
  ]
}
Fetched 5 record(s) in 3ms
// Página 2
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find().limit(5).skip(5*1)
{
  "_id": ObjectId("564a7c362c153ed825a69059"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.312310",
  "defense": 65,
  "height": "12",
  "hp": 65,
  "name": "Fearow",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905a"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905b"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.313816",
  "defense": 44,
  "height": "20",
  "hp": 35,
  "name": "Ekans",
  "speed": 55,
  "types": [
    "poison"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905c"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.318944",
  "defense": 55,
  "height": "8",
  "hp": 60,
  "name": "Raichu",
  "speed": 110,
  "types": [
    "electric"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905d"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.315504",
  "defense": 69,
  "height": "35",
  "hp": 60,
  "name": "Arbok",
  "speed": 80,
  "types": [
    "poison"
  ]
}
Fetched 5 record(s) in 4ms


// Página 3
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find().limit(5).skip(5*2)
{
  "_id": ObjectId("564a7c372c153ed825a6905e"),
  "attack": 50,
  "created": "2013-11-03T15:05:41.388462",
  "defense": 40,
  "height": "6",
  "hp": 40,
  "name": "Poliwag",
  "speed": 90,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a6905f"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.390744",
  "defense": 65,
  "height": "10",
  "hp": 65,
  "name": "Poliwhirl",
  "speed": 90,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69060"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.393388",
  "defense": 95,
  "height": "13",
  "hp": 90,
  "name": "Poliwrath",
  "speed": 70,
  "types": [
    "fighting",
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69061"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.396006",
  "defense": 15,
  "height": "9",
  "hp": 25,
  "name": "Abra",
  "speed": 90,
  "types": [
    "psychic"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69062"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.398045",
  "defense": 30,
  "height": "13",
  "hp": 40,
  "name": "Kadabra",
  "speed": 105,
  "types": [
    "psychic"
  ]
}
Fetched 5 record(s) in 3ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.group({
...     initial: {
...         total: 0
...     }
...     , reduce: function(curr, result) {
...     curr.types.forEach(function(type) {
...         if (result[type]) {
...             result[type]++;
...         } else {
...             result[type] = 1;
...         }
...         result.total++;
...     });
... }
... })
[
  {
    "total": 934,
    "poison": 54,
    "bug": 58,
    "normal": 79,
    "flying": 81,
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

//com aggregate, usando $unwind

dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.aggregate([{$unwind: "$types"}, { $group: { _id: "$types", count: {$sum: 1} } } ])
{
  "result": [
    {
      "_id": "dragon",
      "count": 30
    },
    {
      "_id": "dark",
      "count": 35
    },
    {
      "_id": "steel",
      "count": 35
    },
    {
      "_id": "rock",
      "count": 42
    },
    {
      "_id": "ice",
      "count": 28
    },
    {
      "_id": "fire",
      "count": 53
    },
    {
      "_id": "ground",
      "count": 53
    },
    {
      "_id": "ghost",
      "count": 34
    },
    {
      "_id": "psychic",
      "count": 61
    },
    {
      "_id": "fighting",
      "count": 42
    },
    {
      "_id": "water",
      "count": 101
    },
    {
      "_id": "electric",
      "count": 47
    },
    {
      "_id": "grass",
      "count": 70
    },
    {
      "_id": "flying",
      "count": 81
    },
    {
      "_id": "normal",
      "count": 79
    },
    {
      "_id": "bug",
      "count": 58
    },
    {
      "_id": "fairy",
      "count": 31
    },
    {
      "_id": "poison",
      "count": 54
    }
  ],
  "ok": 1
}


```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
-> .count -- só tipo fogo
-> .count -- só de quantos tem a defesa maior que 70

```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.count()
620
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.count({types: "fire"})
53
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.count({defense: {$gt: 70}})
263
```
