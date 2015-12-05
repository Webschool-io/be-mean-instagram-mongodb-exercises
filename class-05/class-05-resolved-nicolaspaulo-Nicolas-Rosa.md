MongoDB - Aula 05 - Exercício
Autor: **Nicolas de Paulo Rosa**

## Importando a collection restaurantes.(1)

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-12T21:25:24.630-0200	connected to: localhost
2015-11-12T21:25:24.631-0200	dropping: be-mean.restaurantes
2015-11-12T21:25:26.160-0200	imported 25359 documents

```

## Importando a collection pokemons.(1)

```
mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2015-12-05T19:11:35.742-0200	connected to: localhost
2015-12-05T19:11:35.743-0200	dropping: be-mean.pokemons
2015-12-05T19:11:35.785-0200	imported 620 documents

```

## Fazendo um distinct por "cuisine" na collection restaurantes.(2)

```
db.restaurantes.distinct("cuisine")
[
  "Hamburgers",
  "Jewish/Kosher",
  "American ",
  "Irish",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
  "Chinese",
  "Other",
  "Chicken",
  "Bakery",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Steak",
  "Italian",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "French",
  "Pizza/Italian",
  "German",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Hotdogs",
  "Seafood",
  "Greek",
  "Not Listed/Not Applicable",
  "African",
  "Japanese",
  "Indian",
  "Thai",
  "Armenian",
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

## Fazendo um distinct por "types" na collection pokemons.(3)

```
db.pokemons.distinct("types")
[
  "flying",
  "normal",
  "electric",
  "water",
  "poison",
  "fighting",
  "psychic",
  "grass",
  "bug",
  "fairy",
  "fire",
  "rock",
  "ground",
  "ice",
  "steel",
  "ghost",
  "dark",
  "dragon"
]

```

## Fazendo as primeiras 3 páginas com .limit() e .skip() de pokemons paginando de 5 em 5.(4)

```
db.pokemons.find().limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 7ms

```

```
db.pokemons.find().limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 3ms

```

```
be-mean> db.pokemons.find().limit(5).skip(5 * 2)
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
  "_id": ObjectId("564a7c372c153ed825a69063"),
  "attack": 80,
  "created": "2013-11-03T15:05:41.402119",
  "defense": 50,
  "height": "8",
  "hp": 70,
  "name": "Machop",
  "speed": 35,
  "types": [
    "fighting"
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
{
  "_id": ObjectId("564a7c372c153ed825a69064"),
  "attack": 100,
  "created": "2013-11-03T15:05:41.404294",
  "defense": 70,
  "height": "15",
  "hp": 80,
  "name": "Machoke",
  "speed": 45,
  "types": [
    "fighting"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69066"),
  "attack": 75,
  "created": "2013-11-03T15:05:41.408658",
  "defense": 35,
  "height": "7",
  "hp": 50,
  "name": "Bellsprout",
  "speed": 40,
  "types": [
    "poison",
    "grass"
  ]
}
Fetched 5 record(s) in 3ms

```
## Fazendo um group() ou aggregate() contando a quantidade de pokemons de cada tipo.(5)

```
db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if (result[type]) {
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... })
... }
... });
[
  {
    "total": 934,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "water": 101,
    "poison": 54,
    "fighting": 42,
    "psychic": 61,
    "grass": 70,
    "bug": 58,
    "fairy": 31,
    "fire": 53,
    "rock": 42,
    "ground": 53,
    "ice": 28,
    "steel": 35,
    "ghost": 34,
    "dark": 35,
    "dragon": 30
  }
]

```

## Fazendo count na collection pokemons de todos.(6)

```
db.pokemons.count()
620

```

## Fazendo count na collection pokemons do tipo fogo.(6)

```
db.pokemons.count({types: "fire"})
53

```

## Fazendo count na collection pokemons de todos com a defesa maior que 70.(6)

```
db.pokemons.count({defense: {$gt: 70}})
263

```
