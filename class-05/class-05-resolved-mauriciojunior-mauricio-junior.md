## MongoDB - Aula 05 resolvido
Autor: Maurício Júnior

## 1 - Importando a collection `restaurantes` e `pokemons`
```
    ➜  class-05 git:(master) mongoimport --host 127.0.0.1 --db be-mean-pokemons-new --collection pokemons --drop --file pokemons.json
    2016-01-30T00:20:20.892-0200    connected to: 127.0.0.1
    2016-01-30T00:20:20.893-0200    dropping: be-mean-pokemons-new.pokemons
    2016-01-30T00:20:20.980-0200    imported 610 documents

    ➜  class-05 git:(master) mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
    2016-01-30T00:20:20.980-0200    connected to: 127.0.0.1
    2016-01-30T00:20:20.980-0200    dropping: be-mean.restaurantes
    2016-01-30T00:20:20.980-0200    imported 25359 documents

```

## 2 - Distinct por `cuisine` na restaurantes
```
    mauriciojunior(mongod-3.0.6) be-mean> db.restaurantes.distinct("cuisine").sort()
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
## 3 - Distinct por `types`no pokemons
```
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.distinct("types").sort()
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

## 4 - As primeiras 3 páginas com `.limit()` e `.skip()` de pokemons (5 em 5)
```
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*0)
    {
      "name": "Rattata"
    }
    {
      "name": "Charmander"
    }
    {
      "name": "Wartortle"
    }
    {
      "name": "Charmeleon"
    }
    {
      "name": "Blastoise"
    }
    Fetched 5 record(s) in 2ms
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*1)
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
      "name": "Kakuna"
    }
    {
      "name": "Spearow"
    }
    Fetched 5 record(s) in 2ms
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*2)
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
      "name": "Seel"
    }
    {
      "name": "Dodrio"
    }
    Fetched 5 record(s) in 2ms
```

## 5 - Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.aggregate([{$unwind: '$types'},{$group: {_id: '$types', total: {$sum: 1}}}])

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

## 6. Realizar 3 counts na pokemons.
```
    mauriciojunior(mongod-3.0.6) be-mean> db.pokemons.count({})
    610

    mauriciojunior(mongod-3.0.6) be-mean> db.pokemons.count({ types: /fire'/i })
    47

    mauriciojunior(mongod-3.0.6) be-mean> db.pokemons.count({ defense: { $gt: 70 } })
    250

```