## MongoDb - Aula 05
Autor: Fernando Lucas

1. Importar as collections `restaurantes` e `pokemons`.
2. Distinct por `cuisine` na restaurantes.
3. Distinct por `types` na pokemons.
4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
5. Group ou Aggregate contando a quantidade de pokemons de cada tipo.
6. Realizar 3 counts na pokemons.


## Estrutura

```md
# MongoDB - Aula 05 - Exercício
User: [GithubUser](link)
Autor: Seu Nome

### Importar as collections `restaurantes` e `pokemons`.
```
➜  be-mean-instagram git:(master) ✗ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file Apostila/classes/mongodb/pokemons.json
2016-05-08T21:42:36.485-0300	connected to: 127.0.0.1
2016-05-08T21:42:36.486-0300	dropping: be-mean.pokemons
2016-05-08T21:42:36.524-0300	imported 610 documents
➜  be-mean-instagram git:(master) ✗ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file Apostila/classes/mongodb/restaurantes.json
2016-05-08T21:42:55.417-0300	connected to: 127.0.0.1
2016-05-08T21:42:55.417-0300	dropping: be-mean.pokemons
2016-05-08T21:42:56.613-0300	imported 25359 documents
```

### Distinct por `cuisine` na restaurantes.
```
fernando(mongod-3.2.6) be-mean> db.pokemons.distinct('cuisine').sort()
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

### Distinct por `types` na pokemons.
```
fernando(mongod-3.2.6) be-mean> db.pokemons.distinct('types').sort()
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

### As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```
fernando(mongod-3.2.6) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Wartortle"
}
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
{
  "name": "Metapod"
}
Fetched 5 record(s) in 2ms
fernando(mongod-3.2.6) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
}
{
  "name": "Rattata"
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
fernando(mongod-3.2.6) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
  "name": "Seel"
}
Fetched 5 record(s) in 1ms
```

### Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
db.pokemons.group({
  initial: {total: 0},
  reduce: function(current, result) {
    current.types.forEach(function(type) {
      if(result[type]) {
        result[type]++;
      } else {
        result[type] = 1;
      }
      result.total++;
      });
  }
  });
[
  {
    "total": 915,
    "water": 105,
    "fire": 47,
    "bug": 61,
    "normal": 78,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "fighting": 38,
    "psychic": 62,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]


 fernando(mongod-3.2.6) be-mean> db.pokemons.aggregate([      {$unwind: '$types'},      {$group: {        _id: '$types',        count: {$sum: 1}        }      }  ]);
  {
    "waitedMS": NumberLong("0"),
    "result": [
      {
        "_id": "grass",
        "count": 75
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
        "_id": "fire",
        "count": 47
      },
      {
        "_id": "ghost",
        "count": 34
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
        "_id": "flying",
        "count": 77
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
      }
    ],
    "ok": 1
  }
```

### Realizar 3 counts na pokemons.
```
fernando(mongod-3.2.6) be-mean> db.pokemons.count()
610
fernando(mongod-3.2.6) be-mean> db.pokemons.count({ types: 'fire'})
47
fernando(mongod-3.2.6) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```
