## 1. Importar as collections restaurantes e pokemons.

``` js
welder@Welder-Mint ~ $ mongoimport --db be-mean --collection pokemons --drop --file /home/welder/Desktop/pokemons.json
2016-01-04T22:20:21.123-0200	connected to: localhost
2016-01-04T22:20:21.133-0200	dropping: be-mean.pokemons
2016-01-04T22:20:21.391-0200	imported 610 documents

welder@Welder-Mint ~ $ mongoimport --db be-mean --collection restaurantes --drop --file /home/welder/Desktop/restaurantes.json
2016-01-04T22:59:36.891-0200	connected to: localhost
2016-01-04T22:59:36.892-0200	dropping: be-mean.restaurantes
2016-01-04T22:59:38.104-0200	imported 25359 documents
welder@Welder-Mint ~ $ 

```

## 2. Distinct por `cuisine` na restaurantes.

``` js
Welder-Mint(mongod-3.2.0) be-mean> r
be-mean.restaurantes
Welder-Mint(mongod-3.2.0) be-mean> r.distinct("cuisine").sort().reverse()
[
  "Vietnamese/Cambodian/Malaysia",
  "Vegetarian",
  "Turkish",
  "Thai",
  "Tex-Mex",
  "Tapas",
  "Steak",
  "Spanish",
  "Southwestern",
  "Soups & Sandwiches",
  "Soups",
  "Soul Food",
  "Seafood",
  "Scandinavian",
  "Sandwiches/Salads/Mixed Buffet",
  "Sandwiches",
  "Salads",
  "Russian",
  "Portuguese",
  "Polynesian",
  "Polish",
  "Pizza/Italian",
  "Pizza",
  "Peruvian",
  "Pancakes/Waffles",
  "Pakistani",
  "Other",
  "Nuts/Confectionary",
  "Not Listed/Not Applicable",
  "Moroccan",
  "Middle Eastern",
  "Mexican",
  "Mediterranean",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Korean",
  "Juice, Smoothies, Fruit Salads",
  "Jewish/Kosher",
  "Japanese",
  "Italian",
  "Irish",
  "Iranian",
  "Indonesian",
  "Indian",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Hotdogs/Pretzels",
  "Hotdogs",
  "Hawaiian",
  "Hamburgers",
  "Greek",
  "German",
  "Fruits/Vegetables",
  "French",
  "Filipino",
  "Ethiopian",
  "English",
  "Egyptian",
  "Eastern European",
  "Donuts",
  "Delicatessen",
  "Czech",
  "Creole/Cajun",
  "Creole",
  "Continental",
  "Chinese/Japanese",
  "Chinese/Cuban",
  "Chinese",
  "Chilean",
  "Chicken",
  "Caribbean",
  "Californian",
  "Cajun",
  "Café/Coffee/Tea",
  "CafÃ©/Coffee/Tea",
  "Brazilian",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Barbecue",
  "Bangladeshi",
  "Bakery",
  "Bagels/Pretzels",
  "Australian",
  "Asian",
  "Armenian",
  "American ",
  "African",
  "Afghan"
]

```

## 3-  Distinct por types na pokemons.

``` js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> d.distinct("types").sort()
[
  "bug",
  "dark",
  "dragon",
  "electric",
  "fairy",
  "fighting",
  "fire",
  "flying",
  "ghost",
  "grass",
  "ground",
  "ice",
  "normal",
  "poison",
  "psychic",
  "rock",
  "steel",
  "water"
]

```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

``` js
Welder-Mint(mongod-3.2.0) be-mean> d.find({},{_id: false,name: true}).limit(5).skip(5 * 0)
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Charmander"
}
{
  "name": "Caterpie"
}
{
  "name": "Butterfree"
}
Fetched 5 record(s) in 16ms
Welder-Mint(mongod-3.2.0) be-mean> d.find({},{_id: false,name: true}).limit(5).skip(5 * 1)
{
  "name": "Metapod"
}
{
  "name": "Spearow"
}
{
  "name": "Blastoise"
}
{
  "name": "Rattata"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 1ms
Welder-Mint(mongod-3.2.0) be-mean> d.find({},{_id: false,name: true}).limit(5).skip(5 * 2)
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
{
  "name": "Magneton"
}
{
  "name": "Doduo"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 2ms

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

``` js
Welder-Mint(mongod-3.2.0) be-mean> d.group({
...   initial: {total: 0},
...   reduce: function(curr, result){
...     curr.types.forEach(function(type){
...       if(result[type]){
...         result[type]++;
...       }else{
...         result[type] = 1;
...       }
...       result.total++;
...     });
...   }
... });
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "normal": 78,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "fighting": 38,
    "psychic": 62,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
] 

```

## 6. Realizar 3 counts na pokemons.

``` js
Welder-Mint(mongod-3.2.0) be-mean> d.count()
610
Welder-Mint(mongod-3.2.0) be-mean> d.count({types: {$in: [/fire/i,/ice/i]}})
71
Welder-Mint(mongod-3.2.0) be-mean> d.count({attack: {$gt: 100}})
99

```
