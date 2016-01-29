## 1. Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/sites/be-mean/be-mean-modulo-mongodb/restaurantes.json

mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/sites/be-mean/be-mean-modulo-mongodb/pokemons.json

```


## 2. Distinct por `cuisine` na restaurantes
```
db.restaurantes.distinct('cuisine')

[
  "Hamburgers",
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
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

db.pokemons.distinct('types')

[
  "fire",
  "normal",
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
db.pokemons.find({}, {name:1, _id: 0}).limit(5).skip(0)

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
{
  "name": "Caterpie"
}

db.pokemons.find({}, {name:1, _id: 0}).limit(5).skip(5)


  "name": "Metapod"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Wartortle"
}
{
  "name": "Kakuna"
}

db.pokemons.find({}, {name:1, _id: 0}).limit(5).skip(10)

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
  "name": "Dodrio"
}

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
[
  {
    "total" : 796,
    "fire" : 41,
    "water" : 92,
    "bug" : 54,
    "flying" : 67,
    "normal" : 59,
    "steel" : 37,
    "electric" : 31,
    "poison" : 45,
    "ice" : 21,
    "fighting" : 33,
    "grass" : 67,
    "ground" : 47,
    "fairy" : 21,
    "psychic" : 55,
    "rock" : 45,
    "dark" : 30,
    "dragon" : 20,
    "ghost" : 31
  }
]

db.pokemons.aggregate(
    { $unwind: "$types" } , 
    {
    $group: {
        _id: {'tipo': "$types"},
        total: { $sum: 1}

    }
    }
)

{
  "result": [
    {
      "_id": {
        "tipo": "fairy"
      },
      "total": 28
    },
    {
      "_id": {
        "tipo": "psychic"
      },
      "total": 62
    },
    {
      "_id": {
        "tipo": "fighting"
      },
      "total": 38
    },
    {
      "_id": {
        "tipo": "dark"
      },
      "total": 38
    },
    {
      "_id": {
        "tipo": "ground"
      },
      "total": 51
    },
    {
      "_id": {
        "tipo": "grass"
      },
      "total": 75
    },
    {
      "_id": {
        "tipo": "electric"
      },
      "total": 40
    },
    {
      "_id": {
        "tipo": "steel"
      },
      "total": 37
    },
    {
      "_id": {
        "tipo": "rock"
      },
      "total": 46
    },
    {
      "_id": {
        "tipo": "flying"
      },
      "total": 77
    },
    {
      "_id": {
        "tipo": "fire"
      },
      "total": 47
    },
    {
      "_id": {
        "tipo": "ice"
      },
      "total": 24
    },
    {
      "_id": {
        "tipo": "bug"
      },
      "total": 61
    },
    {
      "_id": {
        "tipo": "poison"
      },
      "total": 54
    },
    {
      "_id": {
        "tipo": "ghost"
      },
      "total": 34
    },
    {
      "_id": {
        "tipo": "dragon"
      },
      "total": 20
    },
    {
      "_id": {
        "tipo": "water"
      },
      "total": 105
    },
    {
      "_id": {
        "tipo": "normal"
      },
      "total": 78
    }
  ],
  "ok": 1
}


```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos

MacMax(mongod-3.0.7) be-mean> db.pokemons.count({})
610

-> .count -- só tipo fogo

MacMax(mongod-3.0.7) be-mean> db.pokemons.count({types: "fire"})
47

-> .count -- só de quantos tem a defesa maior que 70

MacMax(mongod-3.0.7) be-mean> db.pokemons.count({defense: { $gte: 70}})
295

