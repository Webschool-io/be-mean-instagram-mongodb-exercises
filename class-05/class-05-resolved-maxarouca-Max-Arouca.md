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
```

## 6. Realizar 3 counts na pokemons.


``` JavaScript
db.pokemons.count({}) // todos

db.pokemons.count({types: 'fire'}) // só tipo fogo

db.pokemons.count({defense: {$gt: 70}}) // só de quantos tem a defesa maior que 70

```
