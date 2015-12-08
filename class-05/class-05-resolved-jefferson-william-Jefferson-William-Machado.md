### MongoDB - Aula 05 - Exercício
autor: Jefferson William Machado

## 1. Importar as collections restaurantes e pokemons
```js
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Downloads/pokemons.json
connected to: 127.0.0.1
2015-12-06T16:26:15.560-0200 dropping: be-mean.pokemons
2015-12-06T16:26:15.591-0200 check 9 620
2015-12-06T16:26:15.591-0200 imported 620 objects

$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Downloads/restaurantes.json
connected to: 127.0.0.1
2015-12-06T16:26:56.263-0200 dropping: be-mean.restaurantes
2015-12-06T16:26:57.578-0200 check 9 25359
2015-12-06T16:26:57.663-0200 imported 25359 objects
```

## 2. Distinct por 'cuisine' na restaurantes
```js
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

## 3.  Distinct por 'types' na pokemons
```js
> db.pokemons.distinct('types')
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
> db.pokemons.find({}).limit(5).skip(5 * 0)
{
    "_id": "ObjectId(\"564a7c362c153ed825a69054\")",
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
    "_id": "ObjectId(\"564a7c362c153ed825a69055\")",
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
    "_id": "ObjectId(\"564a7c362c153ed825a69056\")",
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
    "_id": "ObjectId(\"564a7c362c153ed825a69057\")",
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
    "_id": "ObjectId(\"564a7c362c153ed825a69058\")",
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
```

## 5. Group ou Aggregate contatando a quantidade de pokemons de cada tipo
```js
> db.pokemons.group({
...     initial: {
...         total: 0,
...     },
...     reduce: function (current, result) {
...         result.total++;
...         current.types.forEach(function (type) {
...             if (result[type]) {
...                 result[type]++;
...             } else {
...                 result[type] = 1;
...             }
...         })
...     }
... })
[
  {
    "total" : 620,
    "poison" : 54,
    "bug" : 58,
    "normal" : 79,
    "flying" : 81,
    "electric" : 47,
    "water" : 101,
    "fighting" : 42,
    "psychic" : 61,
    "grass" : 70,
    "fairy" : 31,
    "fire" : 53,
    "rock" : 42,
    "ice" : 28,
    "ground" : 53,
    "steel" : 35,
    "ghost" : 34,
    "dark" : 35,
    "dragon" : 30
  }
]
```

## 6. Realizar 3 counts na pokemons
```js
> db.pokemons.count({})
620
> db.pokemons.count({ types: 'fire' })
53
> db.pokemons.count({ defense: { $gt: 70 } })
263
```