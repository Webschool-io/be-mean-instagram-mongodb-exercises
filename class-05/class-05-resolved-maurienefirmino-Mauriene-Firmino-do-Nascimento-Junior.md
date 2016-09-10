#MongoDB - Aula 05 - Exercícios
autor: Mauriene Firmino

##1. Importar as collections restaurantes e pokemons

```
mauriene@mauriene-J1800NH:~$ mongoimport --db db-aula-05 --collection pokemons --file /home/mauriene/pokemons.json
connected to: 127.0.0.1
2016-09-02T09:18:33.096-0300 check 9 620
2016-09-02T09:18:33.100-0300 imported 620 objects
mauriene@mauriene-J1800NH:~$ mongoimport --db db-aula-05 --collection restaurantes --file /home/mauriene/restaurantes.json
connected to: 127.0.0.1
2016-09-02T09:18:52.012-0300    Progress: 6973897/11906303  58%
2016-09-02T09:18:52.013-0300      12900 4300/second
2016-09-02T09:18:53.470-0300 check 9 25359
2016-09-02T09:18:53.587-0300 imported 25359 objects
mauriene@mauriene-J1800NH:~$ 

```

##2. Distinct por `cuisine` na restaurantes

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.restaurantes.distinct("cuisine")
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

##3. Distinct por `types` na pokemons

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.distinct("types")
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

##4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find().limit(5).skip(5 * 1)
{
  "_id": ObjectId("564a7c362c153ed825a69059"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.312310",
  "defense": 65,
  "height": "12",
  "hp": 65,
  "name": "Fearow",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905a"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905b"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.313816",
  "defense": 44,
  "height": "20",
  "hp": 35,
  "name": "Ekans",
  "speed": 55,
  "types": [
    "poison"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905c"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.318944",
  "defense": 55,
  "height": "8",
  "hp": 60,
  "name": "Raichu",
  "speed": 110,
  "types": [
    "electric"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a6905d"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.315504",
  "defense": 69,
  "height": "35",
  "hp": 60,
  "name": "Arbok",
  "speed": 80,
  "types": [
    "poison"
  ]
}
Fetched 5 record(s) in 6ms

```

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find().limit(5).skip(5 * 2)
{
  "_id": ObjectId("564a7c372c153ed825a6905e"),
  "attack": 50,
  "created": "2013-11-03T15:05:41.388462",
  "defense": 40,
  "height": "6",
  "hp": 40,
  "name": "Poliwag",
  "speed": 90,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a6905f"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.390744",
  "defense": 65,
  "height": "10",
  "hp": 65,
  "name": "Poliwhirl",
  "speed": 90,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69060"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.393388",
  "defense": 95,
  "height": "13",
  "hp": 90,
  "name": "Poliwrath",
  "speed": 70,
  "types": [
    "fighting",
    "water"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69061"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.396006",
  "defense": 15,
  "height": "9",
  "hp": 25,
  "name": "Abra",
  "speed": 90,
  "types": [
    "psychic"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69062"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.398045",
  "defense": 30,
  "height": "13",
  "hp": 40,
  "name": "Kadabra",
  "speed": 105,
  "types": [
    "psychic"
  ]
}
Fetched 5 record(s) in 4ms
mauriene-J1800NH(mongod-2.6.10) db-aula-05> 

```

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find().limit(5).skip(5 * 3)
{
  "_id": ObjectId("564a7c372c153ed825a69063"),
  "attack": 80,
  "created": "2013-11-03T15:05:41.402119",
  "defense": 50,
  "height": "8",
  "hp": 70,
  "name": "Machop",
  "speed": 35,
  "types": [
    "fighting"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69064"),
  "attack": 100,
  "created": "2013-11-03T15:05:41.404294",
  "defense": 70,
  "height": "15",
  "hp": 80,
  "name": "Machoke",
  "speed": 45,
  "types": [
    "fighting"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69065"),
  "attack": 130,
  "created": "2013-11-03T15:05:41.406521",
  "defense": 80,
  "height": "16",
  "hp": 90,
  "name": "Machamp",
  "speed": 55,
  "types": [
    "fighting"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69066"),
  "attack": 75,
  "created": "2013-11-03T15:05:41.408658",
  "defense": 35,
  "height": "7",
  "hp": 50,
  "name": "Bellsprout",
  "speed": 40,
  "types": [
    "poison",
    "grass"
  ]
}
{
  "_id": ObjectId("564a7c372c153ed825a69067"),
  "attack": 62,
  "created": "2013-11-03T15:05:41.265680",
  "defense": 63,
  "height": "10",
  "hp": 60,
  "name": "Ivysaur",
  "speed": 60,
  "types": [
    "poison",
    "grass"
  ]
}
Fetched 5 record(s) in 4ms

```

##5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.aggregate([
...   {$unwind: "$types"},
...   {
...     $group: {
...       _id: '$types',
...       total: {$sum: 1}
...     }
...   },
...   {$project: { _id: 0, tipo: "$_id", total: 1 } }
... ]);
{
  "result": [
    {
      "total": 34,
      "tipo": "ghost"
    },
    {
      "total": 35,
      "tipo": "steel"
    },
    {
      "total": 28,
      "tipo": "ice"
    },
    {
      "total": 53,
      "tipo": "fire"
    },
    {
      "total": 31,
      "tipo": "fairy"
    },
    {
      "total": 61,
      "tipo": "psychic"
    },
    {
      "total": 42,
      "tipo": "fighting"
    },
    {
      "total": 35,
      "tipo": "dark"
    },
    {
      "total": 53,
      "tipo": "ground"
    },
    {
      "total": 70,
      "tipo": "grass"
    },
    {
      "total": 47,
      "tipo": "electric"
    },
    {
      "total": 42,
      "tipo": "rock"
    },
    {
      "total": 81,
      "tipo": "flying"
    },
    {
      "total": 79,
      "tipo": "normal"
    },
    {
      "total": 30,
      "tipo": "dragon"
    },
    {
      "total": 101,
      "tipo": "water"
    },
    {
      "total": 54,
      "tipo": "poison"
    },
    {
      "total": 58,
      "tipo": "bug"
    }
  ],
  "ok": 1
}

```

##6. Realizar 3 counts na pokemons


```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find().count()
620
```

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find({types:["fire"]}).count()
24
```

```
mauriene-J1800NH(mongod-2.6.10) db-aula-05> db.pokemons.find({defense:{$gt:70}}).count()
263
```