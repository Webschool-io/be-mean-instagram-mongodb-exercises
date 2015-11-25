# MongoDB - Aula 05 - Exercício
Autor: Thais Zambe

## 1. Importar as collections restaurantes e pokemons
```js
~ mongoimport --db be-mean-restaurantes --collection restaurantes --drop --file ./Documentos/GitHub/be-mean-instagram/apostila/module-mongodb/data/restaurantes.json
2015-11-22T15:25:14.178-0200    connected to: localhost
2015-11-22T15:25:14.178-0200    dropping: be-mean-restaurantes.restaurantes
2015-11-22T15:25:15.183-0200    imported 25359 documents
```

```js
~ mongoimport --db be-mean-pokemons --collection pokemonseed --drop --file ./Documentos/GitHub/be-mean-instagram/apostila/module-mongodb/data/pokemons.json
2015-11-22T15:26:20.925-0200    connected to: localhost
2015-11-22T15:26:20.925-0200    dropping: be-mean-pokemons.pokemonseed
2015-11-22T15:26:20.945-0200    imported 610 documents
```

## 2. Distinct por `cuisine` na restaurantes
```js
wolkenritter(mongod-3.0.6) be-mean-restaurantes> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Bakery",
  "American ",
  "Hamburgers",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Turkish",
  "Donuts",
  "Caribbean",
  "Sandwiches/Salads/Mixed Buffet",
  "Continental",
  "Pizza",
  "Italian",
  "Bagels/Pretzels",
  "Polish",
  "German",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Steak",
  "French",
  "Mexican",
  "Pizza/Italian",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Soul Food",
  "Pancakes/Waffles",
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
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.distinct('types')
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "electric",
  "steel",
  "ice",
  "ghost",
  "poison",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.find().limit(5).skip(5*0)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
Fetched 5 record(s) in 1ms
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.find().limit(5).skip(5*1)
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ]
}
Fetched 5 record(s) in 2ms
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.find().limit(5).skip(5*2)
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.441502",
  "defense": 45,
  "height": "14",
  "hp": 35,
  "name": "Doduo",
  "speed": 75,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "attack": 110,
  "created": "2013-11-03T15:05:41.443720",
  "defense": 70,
  "height": "18",
  "hp": 60,
  "name": "Dodrio",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
Fetched 5 record(s) in 1ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.aggregate([
...   { $unwind:'$types' },
...   { $group: {
...       _id: { tipo:'$types' },
...       quantidade: { $sum:1 }
...     }
...   }
... ])
{
  "result": [
    {
      "_id": {
        "tipo": "fairy"
      },
      "quantidade": 28
    },
    {
      "_id": {
        "tipo": "fighting"
      },
      "quantidade": 38
    },
    {
      "_id": {
        "tipo": "psychic"
      },
      "quantidade": 62
    },
    {
      "_id": {
        "tipo": "bug"
      },
      "quantidade": 61
    },
    {
      "_id": {
        "tipo": "poison"
      },
      "quantidade": 54
    },
    {
      "_id": {
        "tipo": "rock"
      },
      "quantidade": 46
    },
    {
      "_id": {
        "tipo": "flying"
      },
      "quantidade": 77
    },
    {
      "_id": {
        "tipo": "fire"
      },
      "quantidade": 47
    },
    {
      "_id": {
        "tipo": "ice"
      },
      "quantidade": 24
    },
    {
      "_id": {
        "tipo": "dark"
      },
      "quantidade": 38
    },
    {
      "_id": {
        "tipo": "ground"
      },
      "quantidade": 51
    },
    {
      "_id": {
        "tipo": "grass"
      },
      "quantidade": 75
    },
    {
      "_id": {
        "tipo": "electric"
      },
      "quantidade": 40
    },
    {
      "_id": {
        "tipo": "steel"
      },
      "quantidade": 37
    },
    {
      "_id": {
        "tipo": "ghost"
      },
      "quantidade": 34
    },
    {
      "_id": {
        "tipo": "dragon"
      },
      "quantidade": 20
    },
    {
      "_id": {
        "tipo": "water"
      },
      "quantidade": 105
    },
    {
      "_id": {
        "tipo": "normal"
      },
      "quantidade": 78
    }
  ],
  "ok": 1
}
```

Para conseguir a quantidade total de tipos foi necessário realizar uma outra query, talvez devido à obrigatoriedade do `_id` no `aggregate()`:
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.aggregate([
...   { $unwind:"$types" },
...   { $group: {
...       _id:null,
...       total: { $sum:1 }
...     }
...   }
... ])
{
  "result": [
    {
      "_id": null,
      "total": 915
    }
  ],
  "ok": 1
}
```

## 6. Realizar 3 counts na pokemons.
- .count -- todos
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.count()
610
```
- .count -- só tipo fogo
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {types: {$in: ['fire']}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.count(query)
47
```
- .count -- só de quantos tem a defesa maior que 70
```js
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {defense: {$gt:70}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemonseed.count(query)
250
```
