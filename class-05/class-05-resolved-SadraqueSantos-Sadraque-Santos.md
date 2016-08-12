#MongoDB - Aula 05 - Exercício
Autor: Sadraque Santos

## 1 - Importar as collections restaurantes e pokemons.
```
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-07-27T11:40:40.994-0300	connected to: 127.0.0.1
2016-07-27T11:40:40.994-0300	dropping: be-mean.restaurantes
2016-07-27T11:40:42.475-0300	imported 25359 documents

mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2016-07-27T11:28:08.879-0300	connected to: 127.0.0.1
2016-07-27T11:28:08.879-0300	dropping: be-mean.pokemons
2016-07-27T11:28:09.424-0300	imported 620 documents
```

## 2 - Distinct por cuisine na restaurantes.
```js
db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Bakery",
  "Hamburgers",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Turkish",
  "Caribbean",
  "Chicken",
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

## 3 - Distinct por types na pokemons;
```js
db.pokemons.distinct('types')
[
  "flying",
  "normal",
  "electric",
  "poison",
  "bug",
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

## 4 - As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5).
```js
var query = {}
var opt = {_id:0}
var lmt = 5
db.pokemons.find(query, opt).limit(lmt).skip(lmt * 0)
{
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
// Fetched 5 record(s) in 3ms
db.pokemons.find(query, opt).limit(lmt).skip(lmt * 1)
{
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
// Fetched 5 record(s) in 6ms
db.pokemons.find(query, opt).limit(lmt).skip(lmt * 2)
{
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
// Fetched 5 record(s) in 1ms
```

## 5 - Um group ou aggregate contando a quantidade de pokemons de cada tipo.
```js
db.pokemons.group({
  initial: {total: 0},
  reduce: function(curr, result) {
    curr.types.forEach(function(type) {
      if(result[type]) {
        result[type]++;
      } else {
        result[type] = 1;
      }
      result.total++;
    });
  }
});

[
  {
    "total": 934,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "poison": 54,
    "bug": 58,
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
```

## 6 - Realizar 3 counts na pokemons.
```js
var query = {}
db.pokemons.count(query)
620

var query = {"types": "fire"}
db.pokemons.count(query)
53

var query = {"defense": {$gt: 70}}
db.pokemons.count(query)
263
```
