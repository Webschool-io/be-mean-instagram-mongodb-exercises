# MongoDB - Aula 05 - Exercício
*autor:* [Jean Martins Rito](http://github.com/rito)

## 1. Importar as collections restaurantes e pokemons

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-11T13:07:34.881-0200	connected to: localhost
2015-11-11T13:07:34.881-0200	dropping: be-mean.restaurantes
2015-11-11T13:07:37.823-0200	[####################....] be-mean.restaurantes	9.8 MB/11.3 MB (86.3%)
2015-11-11T13:07:38.731-0200	imported 25359 documents

```
```
mongoimport --db be-mean --collection pokemons --drop --file poks.json
2015-11-30T22:33:37.377-0200	connected to: localhost
2015-11-30T22:33:37.390-0200	dropping: be-mean.pokemons
2015-11-30T22:33:38.398-0200	imported 610 documents

```
## 2. Distinct por `cuisine` na restaurantes.
```
db.restaurantes.distinct('cuisine').sort()

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

## 3. Distinct por `types` na pokemons.

```
db.pokemons.distinct('types').sort()


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

```
db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 0)

{
  "name": "Rattata"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
{
  "name": "Wartortle"
}
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 31ms
Mockingjay(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Metapod"
}
{
  "name": "Charmander"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Farfetchd"
}
Fetched 5 record(s) in 23ms
Mockingjay(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Magnemite"
}
{
  "name": "Kakuna"
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
Fetched 5 record(s) in 35ms

```

## 4. Group ou Aggregate contando a quantidade de pokemons de cada tipo.

```

db.pokemons.aggregate([
  {
    $unwind: "$types"
  }
  , {
    $group: {
      _id: "$types"
      , total: { $sum: 1 }
    }
  }
]);



{
  "result": [
    {
      "_id": "fairy",
      "total": 28
    },
    {
      "_id": "fighting",
      "total": 38
    },
    {
      "_id": "psychic",
      "total": 62
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
    },
    {
      "_id": "normal",
      "total": 78
    }
  ],
  "ok": 1
}




```


## 5. Realizar 3 counts na pokemons.

### 5.1 - Todos
```
db.pokemons.count()

611
```

### 5.2 - Só do tipo "Fogo"
```
db.pokemons.count({types: 'fire'})

47
```
### 5.3 - ó de quantos tem a defesa maior que 70?
```
db.pokemons.count({defense: {$gt: 70}})

250

```
