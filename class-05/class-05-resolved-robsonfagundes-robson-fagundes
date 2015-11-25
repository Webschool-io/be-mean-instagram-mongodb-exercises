# MongoDB - Aula 05 - Exercício
autor: Robson Fagundes

## 1. Importar as collections restaurantes e pokemons

```js
robsonfagundes@Dell-3500:~$ mongoimport --db be-mean-restaurantes --collection restaurantes --drop --file restaurantes.json
2015-11-23T19:07:15.114-0200    connected to: localhost
2015-11-23T19:07:15.115-0200    dropping: be-mean-restaurantes.restaurantes
2015-11-23T19:07:18.123-0200    [###################.....] be-mean-restaurantes.restaurantes    9.3 MB/11.4 MB (82.1%)
2015-11-23T19:07:19.462-0200    imported 25359 documents

robsonfagundes@Dell-3500:~$ mongoimport --db be-mean-pokemons --collection pokemons --drop --file pokemons.json
2015-11-23T19:11:35.603-0200    connected to: localhost
2015-11-23T19:11:35.604-0200    dropping: be-mean-pokemons.pokemons
2015-11-23T19:11:35.686-0200    imported 610 documents
```

## 2. Distinct por `cuisine` na collection restaurantes

```js
Dell-3500(mongod-3.0.7) be-mean-restaurantes> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Hamburgers",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
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

## 3. Distinct por `types` na pokemons

```js
Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "flying",
  "normal",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
  "fighting",
  "psychic",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```js
Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {name : 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Charmander"
}
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
Fetched 5 record(s) in 2ms

Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {name : 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Butterfree"
}
{
  "name": "Wartortle"
}
{
  "name": "Rattata"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 2ms

Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {name : 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Magneton"
}
{
  "name": "Magnemite"
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
Fetched 5 record(s) in 2ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.aggregate([
...     { $unwind: '$types'},
...     {
...         $group: {
...             _id: "$types",
...             total: { $sum: 1 }
...         }
...     }
... ])
{
  "result": [
    {
      "_id": "fairy",
      "total": 28
    },
    {
      "_id": "psychic",
      "total": 62
    },
    {
      "_id": "fighting",
      "total": 38
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
      "_id": "normal",
      "total": 78
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
Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({})
610

Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({types: 'fire'})
47

Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({defense: {$gt: 70}, types: 'fire'})
15

Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.count({types: 'fire', defense: {$gte: 70}})
19
```

