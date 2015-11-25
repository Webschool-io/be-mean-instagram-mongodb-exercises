# MongoDB - Aula 05 - Exercício
autor: **Thiago Aurélio da Cunha**

## Importar as collections restaurantes e pokemons

    ```
     MacBook:bin thiagocunha$ mongoimport --db be-mean --collection restaurantes  --file /Users/thiagocunha/Desktop/mongo/bin/restaurantes.json
     2015-11-16T13:42:08.324-0200	connected to: localhost
     2015-11-16T13:42:09.667-0200	imported 25359 documents

    MacBook:bin thiagocunha$ mongoimport --db be-mean --collection pokemons --file /Users/thiagocunha/Desktop/mongo/bin/pokemons.json
    2015-11-24T19:49:06.499-0200	connected to: localhost
    2015-11-24T19:49:06.518-0200	imported 610 documents
    ```

## Distinct por cuisine na collection restaurante

    ```
    MacBook(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine');
    [
      "Hamburgers",
      "Bakery",
      "Irish",
      "American ",
      "Jewish/Kosher",
      "Delicatessen",
      "Ice Cream, Gelato, Yogurt, Ices",
      "Other",
      "Chinese",
      "Chicken",
      "Turkish",
      "Caribbean",
      "Sandwiches/Salads/Mixed Buffet",
      "Bagels/Pretzels",
      "Continental",
      "Pizza",
      "Donuts",
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
      "Greek",
      "Not Listed/Not Applicable",
      "African",
      "Hotdogs",
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
    MacBook(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine').length;
    85


    ```
    
## Distinct por types na collection pokemons

    ```
    MacBook(mongod-3.0.7) be-mean> db.pokemons.distinct('types').sort();
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
    MacBook(mongod-3.0.7) be-mean> db.pokemons.distinct('types').length;
    18
    ```
## As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)

    ```
    MacBook(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip();
    {
      "name": "Squirtle"
    }
    {
      "name": "Rattata"
    }
    {
      "name": "Wartortle"
    }
    {
      "name": "Caterpie"
    }
    {
      "name": "Blastoise"
    }
    Fetched 5 record(s) in 12ms
    MacBook(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1);
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
    {
      "name": "Farfetchd"
    }
    Fetched 5 record(s) in 9ms
    MacBook(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 3);
    {
      "name": "Magneton"
    }
    {
      "name": "Dodrio"
    }
    {
      "name": "Dewgong"
    }
    {
      "name": "Gastly"
    }
    {
      "name": "Poliwhirl"
    }
    Fetched 5 record(s) in 2ms
    ```
## Group ou Aggregate contando a quantidade de pokemons de cada tipo

    ```
    var aggregate = [{$unwind: "$types"}, {$group: {_id: "$types", count: {$sum: 1}}}]
    MacBook(mongod-3.0.7) be-mean> db.pokemons.aggregate(aggregate)
    {
      "result": [
        {
          "_id": "fairy",
          "count": 28
        },
        {
          "_id": "psychic",
          "count": 62
        },
        {
          "_id": "fighting",
          "count": 38
        },
        {
          "_id": "dark",
          "count": 38
        },
        {
          "_id": "ground",
          "count": 51
        },
        {
          "_id": "grass",
          "count": 75
        },
        {
          "_id": "electric",
          "count": 40
        },
        {
          "_id": "steel",
          "count": 37
        },
        {
          "_id": "ice",
          "count": 24
        },
        {
          "_id": "fire",
          "count": 47
        },
        {
          "_id": "rock",
          "count": 46
        },
        {
          "_id": "flying",
          "count": 77
        },
        {
          "_id": "bug",
          "count": 61
        },
        {
          "_id": "poison",
          "count": 54
        },
        {
          "_id": "ghost",
          "count": 34
        },
        {
          "_id": "dragon",
          "count": 20
        },
        {
          "_id": "water",
          "count": 105
        },
        {
          "_id": "normal",
          "count": 78
        }
      ],
      "ok": 1
    }

    ```
## Realizar 3 counts na pokemons

    ```
    MacBook(mongod-3.0.7) be-mean> db.pokemons.count()
    612
    ```
    ```
    MacBook(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
    47
    ```
    ```
    MacBook(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
    250
    ```