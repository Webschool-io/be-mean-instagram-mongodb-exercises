## 1. Importar as collections restaurantes e pokemons.

``` JavaScript
bin monkey_001$ ./mongoimport --db be-mean --collection pokemons --drop --file "exercicios/exercicio5/pokemons.json"
2015-12-13T18:11:57.428-0200  connected to: localhost
2015-12-13T18:11:57.468-0200  dropping: be-mean.pokemons
2015-12-13T18:11:57.733-0200  imported 620 documents
```

## 2. Distinct por `cuisine` na restaurantes.

``` JavaScript
Monkey-2(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "American ",
  "Irish",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
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

## 3-  Distinct por types na pokemons.

``` JavaScript
Monkey-2(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
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

``` JavaScript
db.pokemons.find() //Todos
db.pokemons.find().limit(5).skip(5 * 0) // Primeira Página
db.pokemons.find().limit(5).skip(5 * 1) // Segunda Página
db.pokemons.find().limit(5).skip(5 * 2) // Terceira Página

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

``` JavaScript
--Agregate--
db.pokemons.aggregate([
  { $unwind: "$types" },
  {
    $group:{
      _id:"$types",
      total: {$sum: 1}
    }  
  }
]);

{
  "result": [
    {
      "_id": "ghost",
      "total": 34
    },
    {
      "_id": "steel",
      "total": 35
    },
    {
      "_id": "ice",
      "total": 28
    },
    {
      "_id": "fire",
      "total": 53
    },
    {
      "_id": "dark",
      "total": 35
    },
    {
      "_id": "ground",
      "total": 53
    },
    {
      "_id": "electric",
      "total": 47
    },
    {
      "_id": "grass",
      "total": 70
    },
    {
      "_id": "psychic",
      "total": 61
    },
    {
      "_id": "fairy",
      "total": 31
    },
    {
      "_id": "fighting",
      "total": 42
    },
    {
      "_id": "poison",
      "total": 54
    },
    {
      "_id": "bug",
      "total": 58
    },
    {
      "_id": "dragon",
      "total": 30
    },
    {
      "_id": "water",
      "total": 101
    },
    {
      "_id": "rock",
      "total": 42
    },
    {
      "_id": "flying",
      "total": 81
    },
    {
      "_id": "normal",
      "total": 79
    }
  ],
  "ok": 1
}
--Group--
db.pokemons.group({
  initial: {count: 0},
  reduce: function(curr, result) {
    curr.types.forEach(function(property) {
      if(result[property])
        result[property]++;
      else
        result[property] = 1;

      result.count++;
    })
  }
})

[
  {
    "count": 934,
    "normal": 79,
    "flying": 81,
    "poison": 54,
    "bug": 58,
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


```

## 6. Realizar 3 counts na pokemons.
``` JavaScript
Monkey-2(mongod-3.0.7) be-mean> db.pokemons.count({})
620

Monkey-2(mongod-3.0.7) be-mean> db.pokemons.count({types:'fire'})
53

Monkey-2(mongod-3.0.7) be-mean> db.pokemons.count({defense:{$gt:70}})
263
```