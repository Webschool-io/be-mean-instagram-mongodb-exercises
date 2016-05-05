# MongoDB - Aula 05- Exercício
autor: C0D3R4

Insert Keys = query,mod, opt, poke ;

## 1. Importar as collections `restaurantes` e `pokemons`.

```JavaScript

devbuntu@devbuntu-Box:/home/be-mean/be-mean-instagram/apostila/module-mongodb/data$ mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
2015-12-03T12:56:10.263+0000 dropping: be-mean.restaurantes
2015-12-03T12:56:11.187+0000 check 9 25359
2015-12-03T12:56:11.826+0000 imported 25359 objects

devbuntu@devbuntu-Box:/home/be-mean/be-mean-instagram/apostila/module-mongodb/data$ mongoimport -d be-mean -c pokemons --drop --file pokemons.json 
connected to: 127.0.0.1
2015-12-03T12:57:52.333+0000 dropping: be-mean.pokemons
2015-12-03T12:57:52.382+0000 check 9 610
2015-12-03T12:57:52.395+0000 imported 610 objects

```

## 2. Distinct por `cuisine` na restaurantes.

```JavaScript

devbuntu-Box(mongod-2.6.3) be-mean> db.restaurantes.distinct('cuisine').sort()
[
  "Afghan",
  "African",
  "American ",
  "Armenian",
  "Asian",
  "Australian",
  "Bagels/Pretzels",
  "Bakery",
  "Bangladeshi",
  "Barbecue",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Brazilian",
  "CafÃ©/Coffee/Tea",
  "Café/Coffee/Tea",
  "Cajun",
  "Californian",
  "Caribbean",
  "Chicken",
  "Chilean",
  "Chinese",
  "Chinese/Cuban",
  "Chinese/Japanese",
  "Continental",
  "Creole",
  "Creole/Cajun",
  "Czech",
  "Delicatessen",
  "Donuts",
  "Eastern European",
  "Egyptian",
  "English",
  "Ethiopian",
  "Filipino",
  "French",
  "Fruits/Vegetables",
  "German",
  "Greek",
  "Hamburgers",
  "Hawaiian",
  "Hotdogs",
  "Hotdogs/Pretzels",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Indian",
  "Indonesian",
  "Iranian",
  "Irish",
  "Italian",
  "Japanese",
  "Jewish/Kosher",
  "Juice, Smoothies, Fruit Salads",
  "Korean",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Mediterranean",
  "Mexican",
  "Middle Eastern",
  "Moroccan",
  "Not Listed/Not Applicable",
  "Nuts/Confectionary",
  "Other",
  "Pakistani",
  "Pancakes/Waffles",
  "Peruvian",
  "Pizza",
  "Pizza/Italian",
  "Polish",
  "Polynesian",
  "Portuguese",
  "Russian",
  "Salads",
  "Sandwiches",
  "Sandwiches/Salads/Mixed Buffet",
  "Scandinavian",
  "Seafood",
  "Soul Food",
  "Soups",
  "Soups & Sandwiches",
  "Southwestern",
  "Spanish",
  "Steak",
  "Tapas",
  "Tex-Mex",
  "Thai",
  "Turkish",
  "Vegetarian",
  "Vietnamese/Cambodian/Malaysia"
]

```

## 3-  Distinct por `types` na pokemons.

```JavaScript

devbuntu-Box(mongod-2.6.3) be-mean> db.pokemons.distinct('types').sort()
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

```JavaScript
db.pokemons.find().limit(5).skip(5 * 0) // Página 1
db.pokemons.find().limit(5).skip(5 * 1) // Página 2
db.pokemons.find().limit(5).skip(5 * 2) // Página 3



```
## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```JavaScript

devbuntu-Box(mongod-2.6.3) be-mean> db.pokemons.group({
...   initial: {total: 0},
...   reduce: function(curr, result) {
...     curr.types.forEach(function(type) {
...       if(result[type])
...         result[type]++;
...       else
...         result[type] = 1;
...       result.total++;
...     })
...   }
... })
[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
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
devbuntu-Box(mongod-2.6.3) be-mean> 


```
## 6. Realizar `3` counts na pokemons.

```JavaScript

devbuntu-Box(mongod-2.6.3) be-mean> db.pokemons.count({types: /fire/i})
47
devbuntu-Box(mongod-2.6.3) be-mean> db.pokemons.count({speed: {$lt:50}})
181
devbuntu-Box(mongod-2.6.3) be-mean> db.pokemons.count()
610
devbuntu-Box(mongod-2.6.3) be-mean> 



```