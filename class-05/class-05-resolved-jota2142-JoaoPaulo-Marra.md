# MongoDB - Aula 05 - Exercício

Autor: João Paulo Costa Marra

## 1. Importar as collections restaurantes e pokemons.

```
Jota@JOTA-PC C:\Users\Jota
> mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file C:\Users\Jota\Desktop\restaurantes.json
2016-02-09T16:04:56.900-0200    connected to: 127.0.0.1
2016-02-09T16:04:56.902-0200    dropping: be-mean.restaurantes
2016-02-09T16:04:59.901-0200    [##############..........] be-mean.restaurantes 6.9 MB/11.4 MB (61.1%)
2016-02-09T16:05:01.576-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-02-09T16:05:01.576-0200    imported 25359 documents
```

```
Jota@JOTA-PC C:\Users\Jota
> mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file C:\Users\Jota\Desktop\pokemons.json
2016-02-09T16:05:46.008-0200    connected to: 127.0.0.1
2016-02-09T16:05:46.009-0200    dropping: be-mean.pokemons
2016-02-09T16:05:46.102-0200    imported 610 documents
```

## 2. Distinct por `cuisine` na restaurantes.

```
Jota-PC(mongod-3.2.1) be-mean> db.restaurantes.distinct("cuisine")
[
  "Hamburgers",
  "Bakery",
  "Jewish/Kosher",
  "American ",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Irish",
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

## 3.  Distinct por `types` na pokemons.

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.distinct("types")
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
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

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5 * 0)
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 64ms

Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 22ms

Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({}, { name: 1, _id: 0 }).limit(5).skip(5 * 2)
{
  "name": "Magnemite"
}
{
  "name": "Farfetchd"
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
Fetched 5 record(s) in 6ms
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.group({ initial: {total: 0}, cond: {defense: {$gt: 40}}, reduce: function(current, result){ current.types.forEach(function(type){ result[type] ? result[type]++ : result[type] = 1; result.total++; }); } });
[
  {
    "total": 796,
    "fire": 41,
    "water": 92,
    "bug": 54,
    "flying": 67,
    "poison": 45,
    "steel": 37,
    "electric": 31,
    "normal": 59,
    "ice": 21,
    "fighting": 33,
    "grass": 67,
    "ground": 47,
    "fairy": 21,
    "psychic": 55,
    "rock": 45,
    "dark": 30,
    "dragon": 20,
    "ghost": 31
  }
]
```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.count({})
610
```
-> .count -- só tipo fogo

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.count({ types: "fire" })
47
```
-> .count -- só de quantos tem a defesa maior que 70

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.count({ defense: { $gt: 70 } })
250
```