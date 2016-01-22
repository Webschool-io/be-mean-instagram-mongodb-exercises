#MongoDB - Aula 05 - Exercícios
autor: Thiago Nogueira

##1. Importar as collections restaurantes e pokemons
```js
~ ❯❯❯ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Desktop/pokemons.json                                                              2016-01-21T17:52:17.706-0300	connected to: 127.0.0.1
2016-01-21T17:52:17.707-0300	dropping: be-mean.pokemons
2016-01-21T17:52:17.851-0300	imported 610 documents
~ ❯❯❯ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Desktop/restaurantes.json                                2016-01-21T21:56:11.250-0300	connected to: 127.0.0.1
2016-01-21T21:56:11.251-0300	dropping: be-mean.restaurantes
2016-01-21T21:56:12.613-0300	imported 25359 documents
```
##2. Dar distinct em restaurantes passando 'cuisine' por parametro.
```js
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.restaurantes.distinct('cuisine')
[
  "American ",
  "Irish",
  "Bakery",
  "Hamburgers",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
  "Chinese",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Pizza",
  "Continental",
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

##3. Dar um distinct em pokemons passando 'types' por parametro.
```js
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.pokemons.distinct('types')
[
  "water",
  "fire",
  "normal",
  "bug",
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
##4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em
```js
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.pokemons.find({},{name: 1, _id: 0}).limit(5).skip(5*0)
{
  "name": "Wartortle"
}
{
  "name": "Charmander"
}
{
  "name": "Rattata"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 1ms
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.pokemons.find({},{name: 1, _id: 0}).limit(5).skip(5*1)
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 2ms
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.pokemons.find({},{name: 1, _id: 0}).limit(5).skip(5*2)
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
{
  "name": "Doduo"
}
{
  "name": "Magneton"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 1ms
```

##5.Um group ou aggregate contando a quantidade de pokemons de cada tipo
```js
TNP-MacBook-Air(mongod-3.2.1) be-mean> db.pokemons.aggregate([
... { $unwind: "$types" }
...   , { $group: {
... _id: "$types"
...   , total: { $sum: 1 }
... }
...   }
... ]);
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
      "_id": "ghost",
      "total": 34
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
      "_id": "flying",
      "total": 77
    },
    {
      "_id": "fire",
      "total": 47
    },
    {
      "_id": "rock",
      "total": 46
    },
    {
      "_id": "water",
      "total": 105
    }
  ],
  "ok": 1
}
```
##6. Realizar count na collection pokemons

```js
6.1 Todos:
db.pokemons.count();
610
```

```js
6.2 Apenas os do `types` `fire`:
db.pokemons.count({ types: "fire"});
47
```

```js
6.3 Apenas os com defesa maior que 70:
db.pokemons.count({ defense: { $gt: 70 }});
250
```
