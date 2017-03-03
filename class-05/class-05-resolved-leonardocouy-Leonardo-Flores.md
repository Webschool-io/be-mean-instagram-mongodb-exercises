# MongoDB - Aula 05 - Exercício
autor: Leonardo Flores

## Importar as collections restaurantes e pokemons
```
MacBook-Pro-de-Leonardo:Exercicio 1 leo$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-03-16T11:36:55.409-0300  connected to: 127.0.0.1
2016-03-16T11:36:55.409-0300  dropping: be-mean.restaurantes
2016-03-16T11:36:56.152-0300  imported 25359 documents

MacBook-Pro-de-Leonardo:MongoDB leo$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2016-03-16T11:37:38.169-0300  connected to: 127.0.0.1
2016-03-16T11:37:38.169-0300  dropping: be-mean.pokemons
2016-03-16T11:37:38.203-0300  imported 610 documents

```

## Fazer um distinct por `cuisine` na collection restaurantes
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "American ",
  "Hamburgers",
  "Irish",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Continental",
  "Bagels/Pretzels",
  "Pizza",
  "Italian",
  "Steak",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "German",
  "French",
  "Pizza/Italian",
  "Spanish",
  "Mexican",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Hotdogs",
  "Greek",
  "Seafood",
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

## Fazer um distinct por `types` na collection pokemons
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "normal",
  "flying",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5*0)
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Rattata"
}
Fetched 5 record(s) in 3ms
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5*1)
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
{
  "name": "Charmander"
}
{
  "name": "Magnemite"
}
Fetched 5 record(s) in 4ms
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5*2)
{
  "name": "Magneton"
}
{
  "name": "Wartortle"
}
{
  "name": "Doduo"
}
{
  "name": "Farfetchd"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 4ms
```

## Apresentar quantidade de pokemons de cada `type` (group ou aggregate)
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.aggregate([
...   {$unwind: "$types"},
...   {$group: {
...     _id: "$types",
...     total: {$sum: 1},
...   }}
... ])
{
  "waitedMS": NumberLong("0"),
  "result": [
    {
      "_id": "grass",
      "total": 75
    },
    {
      "_id": "dark",
      "total": 38
    },
    {
      "_id": "fairy",
      "total": 28
    },
    {
      "_id": "psychic",
      "total": 62
    },
    {
      "_id": "electric",
      "total": 40
    },
    {
      "_id": "dragon",
      "total": 20
    },
    {
      "_id": "bug",
      "total": 61
    },
    {
      "_id": "steel",
      "total": 37
    },
    {
      "_id": "ice",
      "total": 24
    },
    {
      "_id": "ground",
      "total": 51
    },
    {
      "_id": "poison",
      "total": 54
    },
    {
      "_id": "fighting",
      "total": 38
    },
    {
      "_id": "normal",
      "total": 78
    },
    {
      "_id": "ghost",
      "total": 34
    },
    {
      "_id": "rock",
      "total": 46
    },
    {
      "_id": "water",
      "total": 105
    },
    {
      "_id": "flying",
      "total": 77
    },
    {
      "_id": "fire",
      "total": 47
    }
  ],
  "ok": 1
}
```

## Realizar 3 counts na pokemons.

** count -- todos **
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.count({})
610
```

** count -- só tipo fogo **
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.count({types: 'fire'})
47
```

** count -- só de quantos tem a defesa maior que 70 **
```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```