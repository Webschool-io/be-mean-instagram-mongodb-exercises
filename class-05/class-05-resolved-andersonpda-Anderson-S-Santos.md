## 1. Importar as collections restaurantes e pokemons.

```
Mac-mini-de-Anderson:Desktop anderson$ mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection restaurantes --drop --file restaurantes.json
2015-11-25T14:23:22.727-0200  connected to: 127.0.0.1
2015-11-25T14:23:22.728-0200  dropping: be-mean-pokemons.restaurantes
2015-11-25T14:23:24.050-0200  imported 25359 documents
```

```
Mac-mini-de-Anderson:Desktop anderson$ mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection pokemons --drop --file pokemons.json
2015-11-25T14:24:08.383-0200  connected to: 127.0.0.1
2015-11-25T14:24:08.383-0200  dropping: be-mean-pokemons.pokemons
2015-11-25T14:24:08.500-0200  imported 620 documents
```

## 2. Distinct por `cuisine` na restaurantes.

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.restaurantes.distinct("cuisine")
[
  "Bakery",
  "Hamburgers",
  "Jewish/Kosher",
  "Irish",
  "American ",
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

## 3.  Distinct por `types` na pokemons.

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.distinct("types")
[
  "flying",
  "normal",
  "bug",
  "poison",
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

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}).limit(5).skip(0)
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

Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}).limit(5).skip(1)
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

Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}).limit(5).skip(2)
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
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.group({
... initial: {total: 0},
... cond: {defense: {$gt: 40}},
... reduce: function(current, result){
... current.types.forEach(function(type){
... result[type] ? result[type]++ : result[type] = 1;
... result.total++;
... });
... }
... });
[
  {
    "total": 810,
    "normal": 60,
    "flying": 71,
    "poison": 45,
    "water": 90,
    "electric": 37,
    "fighting": 37,
    "grass": 62,
    "fairy": 24,
    "psychic": 53,
    "bug": 50,
    "fire": 46,
    "rock": 41,
    "ice": 23,
    "ground": 48,
    "steel": 35,
    "ghost": 31,
    "dark": 28,
    "dragon": 29
  }
]
```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({})
620
```
-> .count -- só tipo fogo

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({ types: "fire" })
53
```
-> .count -- só de quantos tem a defesa maior que 70

```
Mac-mini-de-Anderson(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({ defense: { $gt: 70 } })
263
```