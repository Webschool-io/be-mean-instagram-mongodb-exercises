# MongoDb - Aula 05 - Exercício
Autor: Hélio Marcondes

## 1. Importar as collections restaurantes e pokemons.

```
    mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/workspace/restaurantes.json
    connected to: 127.0.0.1
    2016-01-28T21:54:03.477+0000 dropping: be-mean.restaurantes
    2016-01-28T21:54:03.596+0000 check 9 25359
    2016-01-28T21:54:03.596+0000 imported 25359 documents

    mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/workspace/pokemons.json
    connected to: 127.0.0.1
    2016-01-28T21:55:53.398+0000 dropping: be-mean.pokemons
    2016-01-28T21:55:53.409+0000 check 9 610
    2016-01-28T21:55:53.409+0000 imported 610 objects

```

## 2. Distinct por cuisine na restaurantes.

```
    db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
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

## 3- Distinct por types na pokemons.

```
    db.pokemons.distinct('types')
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
    db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
    { "name" : "Rattata" }
    { "name" : "Charmander" }
    { "name" : "Charmeleon" }
    { "name" : "Wartortle" }
    { "name" : "Blastoise" }

    db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
    { "name" : "Caterpie" }
    { "name" : "Metapod" }
    { "name" : "Butterfree" }
    { "name" : "Spearow" }
    { "name" : "Kakuna" }

    db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
    { "name" : "Farfetchd" }
    { "name" : "Magnemite" }
    { "name" : "Magneton" }
    { "name" : "Doduo" }
    { "name" : "Seel" }

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
    db.pokemons.group({
    initial: {},
    reduce: function(current, result) {
    current.types.forEach(function(type) {
        if (result[type]) {
        result[type]++;
        } else {
        result[type] = 1;
        }
    });
    }
    });

    [
        {
                "normal" : 78,
                "fire" : 47,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "ice" : 24,
                "ghost" : 34,
                "fighting" : 38,
                "psychic" : 62,
                "grass" : 75,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }
]

```

## 6. Realizar 3 counts na pokemons.

```
    db.pokemons.count()
    610

    db.pokemons.count({types:'fire'})
    47

    db.pokemons.count({types:'dragon'})
    20

```