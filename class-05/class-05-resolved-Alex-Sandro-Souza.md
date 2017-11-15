# MongoDB - Aula 05 - Exercício
autor: Alex Sandro Souza

## 1. Importar as collections restaurantes e pokemons

## Restaurantes
```
eudigitalis@gigantus ~/Downloads$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2017-11-15T12:05:57.443-0200	connected to: localhost
2017-11-15T12:05:57.444-0200	dropping: be-mean.restaurantes
2017-11-15T12:05:58.379-0200	imported 25359 documents

```
## Pokemons
```
eudigitalis@gigantus ~/Downloads$ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2017-11-15T12:04:58.892-0200	connected to: localhost
2017-11-15T12:04:58.893-0200	dropping: be-mean.pokemons
2017-11-15T12:04:58.926-0200	imported 610 documents

```

## 2. Distinct por `cuisine` na restaurantes
```
gigantus(mongod-3.4.10) be-mean> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Hamburgers",
  "Jewish/Kosher",
  "American ",
  "Bakery",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Chinese",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Italian",
  "Donuts",
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
  "Greek",
  "Hotdogs",
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

## 3. Distinct por `types` na pokemons

```
gigantus(mongod-3.4.10) be-mean> db.pokemons.distinct('types')
[
  "bug",
  "flying",
  "water",
  "normal",
  "fire",
  "electric",
  "steel",
  "poison",
  "ice",
  "psychic",
  "fighting",
  "grass",
  "ground",
  "ghost",
  "fairy",
  "rock",
  "dark",
  "dragon"
]


```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
### Page 1

```
gigantus(mongod-3.4.10) be-mean> let paginaAtual = 0;
gigantus(mongod-3.4.10) be-mean> let pokemonsPorPagina = 5;
gigantus(mongod-3.4.10) be-mean> db.pokemons.find().limit(pokemonsPorPagina).skip(pokemonsPorPagina * paginaAtual)
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
Fetched 5 record(s) in 8ms
gigantus(mongod-3.4.10) be-mean> paginaAtual = 1;
1
gigantus(mongod-3.4.10) be-mean> db.pokemons.find().limit(pokemonsPorPagina).skip(pokemonsPorPagina * paginaAtual)
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
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
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
Fetched 5 record(s) in 5ms
gigantus(mongod-3.4.10) be-mean> paginaAtual = 2;
2
gigantus(mongod-3.4.10) be-mean> db.pokemons.find().limit(pokemonsPorPagina).skip(pokemonsPorPagina * paginaAtual)
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
{
  "_id": ObjectId("564b1dae25337263280d0489"),
  "attack": 70,
  "created": "2013-11-03T15:05:41.447897",
  "defense": 80,
  "height": "17",
  "hp": 90,
  "name": "Dewgong",
  "speed": 70,
  "types": [
    "water",
    "ice"
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
  "_id": ObjectId("564b1daf25337263280d048d"),
  "attack": 50,
  "created": "2013-11-03T15:05:41.388462",
  "defense": 40,
  "height": "6",
  "hp": 40,
  "name": "Poliwag",
  "speed": 90,
  "types": [
    "water"
  ]
}
Fetched 5 record(s) in 3ms


```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

### Aggregate

```
gigantus(mongod-3.4.10) be-mean> db.pokemons.aggregate([
...     {
...         $unwind: "$types"
...
...     },
...     {
...         $group: {
...             _id: '$types',
...             count: { $sum: 1 }
...
...         }
...
...     }
... ])
{
  "result": [
    {
      "_id": "ghost",
      "count": 34
    },
    {
      "_id": "grass",
      "count": 75
    },
    {
      "_id": "fighting",
      "count": 38
    },
    {
      "_id": "normal",
      "count": 78
    },
    {
      "_id": "rock",
      "count": 46
    },
    {
      "_id": "water",
      "count": 105
    },
    {
      "_id": "flying",
      "count": 77
    },
    {
      "_id": "fire",
      "count": 47
    },
    {
      "_id": "dragon",
      "count": 20
    },
    {
      "_id": "bug",
      "count": 61
    },
    {
      "_id": "steel",
      "count": 37
    },
    {
      "_id": "electric",
      "count": 40
    },
    {
      "_id": "ground",
      "count": 51
    },
    {
      "_id": "poison",
      "count": 54
    },
    {
      "_id": "ice",
      "count": 24
    },
    {
      "_id": "dark",
      "count": 38
    },
    {
      "_id": "fairy",
      "count": 28
    },
    {
      "_id": "psychic",
      "count": 62
    }
  ],
  "ok": 1
}


```

## 6. Realizar 3 counts na pokemons.
### count -- todos

```
gigantus(mongod-3.4.10) be-mean> db.pokemons.count()
610

```
### count -- só tipo fogo

```
gigantus(mongod-3.4.10) be-mean> db.pokemons.count({types:'fire'})
47
```
### count -- só de quantos tem a defesa maior que 70

```
gigantus(mongod-3.4.10) be-mean> db.pokemons.count({defense:{$gt:70}})
250
```
