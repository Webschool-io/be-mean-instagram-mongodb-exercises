# MongoDB - Aula 05 - Exercício
autor: Wellerson Roberto

## Importar as collections restaurantes e pokemons
```
C:\Users\Wellerson>mongoimport --db mongoAula05 --drop --file "D:\Developer\Curso Mean\exercícios-be-mean\pokemon.json" --collection pokemons
2015-12-03T02:51:17.495-0200    connected to: localhost
2015-12-03T02:51:17.497-0200    dropping: mongoAula05.pokemons
2015-12-03T02:51:17.732-0200    imported 620 documents

C:\Users\Wellerson>mongoimport --db mongoAula05 --drop --file "D:\Developer\Curso Mean\exercícios-be-mean\restaurantes.json" --collection restaurantes
2015-12-03T02:52:48.708-0200    connected to: localhost
2015-12-03T02:52:48.710-0200    dropping: mongoAula05.restaurantes
2015-12-03T02:52:50.153-0200    imported 25359 documents
```

## **Distinct** por 'cuisine' nos restaurantes##
```
> db.restaurantes.distinct("cuisine")
[
        "Hamburgers",
        "Jewish/Kosher",
        "American ",
        "Delicatessen",
        "Irish",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Chicken",
        "Turkish",
        "Bakery",
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
>
```

## Distinct por 'types' na Pokemon ##
```
> db.pokemons.distinct("types")
[
        "bug",
        "poison",
        "flying",
        "normal",
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

## As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)##
```
> db.pokemons.find().skip(5*0).limit(5)
{ "_id" : ObjectId("564a7c362c153ed825a69054"), "attack" : 90, "created" : "2013-11-03T15:05:41.297180", "defense" : 40, "height" : "10", "hp" : 65, "name" : "Beedrill", "speed" : 75, "types" : [ "poison", "bug" ] }
{ "_id" : ObjectId("564a7c362c153ed825a69057"), "attack" : 80, "created" : "2013-11-03T15:05:41.303569", "defense" : 75, "height" : "15", "hp" : 83, "name" : "Pidgeot", "speed" : 101, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564a7c362c153ed825a69058"), "attack" : 81, "created" : "2013-11-03T15:05:41.308092", "defense" : 60, "height" : "7", "hp" : 55, "name" : "Raticate", "speed" : 97, "types" : [ "normal" ] }
{ "_id" : ObjectId("564a7c362c153ed825a69059"), "attack" : 90, "created" : "2013-11-03T15:05:41.312310", "defense" : 65, "height" : "12", "hp" : 65, "name" : "Fearow", "speed" : 100, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905a"), "attack" : 55, "created" : "2013-11-03T15:05:41.317235", "defense" : 40, "height" : "4", "hp" : 35, "name" : "Pikachu", "speed" : 90, "types" : [ "electric" ] }

> db.pokemons.find().skip(5*1).limit(5)
{ "_id" : ObjectId("564a7c362c153ed825a6905b"), "attack" : 60, "created" : "2013-11-03T15:05:41.313816", "defense" : 44, "height" : "20", "hp" : 35, "name" : "Ekans", "speed" : 55, "types" : [ "poison" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905c"), "attack" : 90, "created" : "2013-11-03T15:05:41.318944", "defense" : 55, "height" : "8", "hp" : 60, "name" : "Raichu", "speed" : 110, "types" : [ "electric" ] }
{ "_id" : ObjectId("564a7c362c153ed825a6905d"), "attack" : 85, "created" : "2013-11-03T15:05:41.315504", "defense" : 69, "height" : "35", "hp" : 60, "name" : "Arbok", "speed" : 80, "types" : [ "poison" ] }
{ "_id" : ObjectId("564a7c372c153ed825a6905e"), "attack" : 50, "created" : "2013-11-03T15:05:41.388462", "defense" : 40, "height" : "6", "hp" : 40, "name" : "Poliwag", "speed" : 90, "types" : [ "water" ] }
{ "_id" : ObjectId("564a7c372c153ed825a6905f"), "attack" : 65, "created" : "2013-11-03T15:05:41.390744", "defense" : 65, "height" : "10", "hp" : 65, "name" : "Poliwhirl", "speed" : 90, "types" : [ "water" ] }

> db.pokemons.find().skip(5*2).limit(5)
{ "_id" : ObjectId("564a7c372c153ed825a69065"), "attack" : 130, "created" : "2013-11-03T15:05:41.406521", "defense" : 80, "height" : "16", "hp" : 90, "name" : "Machamp", "speed" : 55, "types" : [ "fighting" ] }
{ "_id" : ObjectId("564a7c372c153ed825a69067"), "attack" : 62, "created" : "2013-11-03T15:05:41.265680", "defense" : 63, "height" : "10", "hp" : 60, "name" : "Ivysaur", "speed" : 60, "types" : [ "poison", "grass" ] }
{ "_id" : ObjectId("564a7c392c153ed825a69068"), "attack" : 95, "created" : "2013-11-03T15:05:41.494714", "defense" : 80, "height" : "22", "hp" : 105, "name" : "Kangaskhan", "speed" : 90, "types" : [ "normal" ] }
{ "_id" : ObjectId("564a7c392c153ed825a69069"), "attack" : 40, "created" : "2013-11-03T15:05:41.496373", "defense" : 70, "height" : "4", "hp" : 30, "name" : "Horsea", "speed" : 60, "types" : [ "water" ] }
{ "_id" : ObjectId("564a7c392c153ed825a6906a"), "attack" : 55, "created" : "2013-11-03T15:05:41.492955", "defense" : 115, "height" : "10", "hp" : 65, "name" : "Tangela", "speed" : 60, "types" : [ "grass" ] }
>
```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo##
```
> db.pokemons.aggregate({$group: {_id: "$types", total: {$sum: 1}}});
{ "_id" : [ "normal", "electric" ], "total" : 1 }
{ "_id" : [ "rock", "ice" ], "total" : 2 }
{ "_id" : [ "rock", "fairy" ], "total" : 1 }
{ "_id" : [ "electric", "fairy" ], "total" : 1 }
{ "_id" : [ "rock", "grass" ], "total" : 1 }
{ "_id" : [ "electric", "dragon" ], "total" : 2 }
{ "_id" : [ "ground", "psychic" ], "total" : 2 }
{ "_id" : [ "ghost", "steel" ], "total" : 3 }
{ "_id" : [ "flying" ], "total" : 1 }
{ "_id" : [ "fighting", "rock" ], "total" : 1 }
{ "_id" : [ "bug", "fire" ], "total" : 2 }
{ "_id" : [ "bug", "ghost" ], "total" : 1 }
{ "_id" : [ "dragon", "dark" ], "total" : 1 }
{ "_id" : [ "flying", "dark" ], "total" : 4 }
{ "_id" : [ "flying", "ghost" ], "total" : 2 }
{ "_id" : [ "ghost", "water" ], "total" : 2 }
{ "_id" : [ "fighting", "steel" ], "total" : 2 }
{ "_id" : [ "grass", "fairy" ], "total" : 2 }
{ "_id" : [ "rock", "dragon" ], "total" : 2 }
{ "_id" : [ "normal", "fighting" ], "total" : 1 }
Type "it" for more
```

## Realizar 3 counts de Pokemons ##

```
> db.pokemons.count()
620
```

```
> db.pokemons.count({types: {$in: ["fire"]}})
53
```

```
> db.pokemons.count({defense: {$gt: 70}})
263
```