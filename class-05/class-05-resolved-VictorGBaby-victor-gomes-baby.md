### MongoDb - Aula 05 - Exercício
autor: Victor Gomes Baby


# 1. Importar as collections restaurantes e pokemons

- Restaurants
MacBook-Pro-de-Victor:be-mean-modulo-mongodb victorgomesbaby$ mongoimport --db be-mean --collection restaurants --file data.json
2015-11-09T23:02:52.851-0200	connected to: localhost
2015-11-09T23:02:55.751-0200	[##########..............] be-mean.restaurants	5.2 MB/11.3 MB (45.5%)
2015-11-09T23:02:56.875-0200	imported 25359 documents

- Pokemons
MacBook-Pro-de-Victor:be-mean-modulo-mongodb victorgomesbaby$ mongoimport --db be-mean --collection 
pokemons --drop --file pokemons.json
2015-11-23T19:19:44.465+0000    connected to: localhost
2015-11-23T19:19:44.466+0000    dropping: be-mean.pokemons
2015-11-23T19:19:44.510+0000    imported 610 documents

# 2. Distinct por 'cuisine' na restaurantes

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.restaurants.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Jewish/Kosher",
  "American ",
  "Irish",
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
  "Steak",
  "Italian",
  "Polish",
  "German",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
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

# 3. Distinct por 'types' 	na pokemons

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
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
  "psychic",
  "fighting",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

- Página 1
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 0)
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
  "name": "Blastoise"
}
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 2ms

- Página 2
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 1)
{
  "name": "Butterfree"
}
{
  "name": "Kakuna"
}
{
  "name": "Wartortle"
}
{
  "name": "Spearow"
}
{
  "name": "Metapod"
}
Fetched 5 record(s) in 25ms

- Página 3
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 2)
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

# 5. Group ou Aggregate contanto a quantidade de pokemons de cada tipo

- Com Group
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.group({
... initial: {total:0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if (result[type]) {
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... });
... }
... });
[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "psychic": 62,
    "fighting": 38,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> 

- Com Aggregate
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.aggregate ({
... $group: {
... _id: '$types',
... total: {$sum:1}
... }
... })
{
  "result": [
    {
      "_id": [
        "steel",
        "dark"
      ],
      "total": 1
    },
    {
      "_id": [
        "ground",
        "ghost"
      ],
      "total": 2
    },
    {
      "_id": [
        "electric",
        "dragon"
      ],
      "total": 1
    },
    {
      "_id": [
        "ghost",
        "steel"
      ],
      "total": 3
    },
    {
      "_id": [
        "rock",
        "dark"
      ],
      "total": 2
    },
    {
      "_id": [
        "ground",
        "steel"
      ],
      "total": 1
    },
    {
      "_id": [
        "fire",
        "psychic"
      ],
      "total": 1
    },
    {
      "_id": [
        "grass",
        "electric"
      ],
      "total": 1
    },
    {
      "_id": [
        "steel",
        "fairy"
      ],
      "total": 1
    },
    {
      "_id": [
        "fighting",
        "poison"
      ],
      "total": 2
    },
    {
      "_id": [
        "fighting",
        "rock"
      ],
      "total": 1
    },
    {
      "_id": [
        "ghost",
        "water"
      ],
      "total": 2
    },
    {
      "_id": [
        "grass",
        "fairy"
      ],
      "total": 2
    },
    {
      "_id": [
        "fighting",
        "steel"
      ],
      "total": 2
    },
    {
      "_id": [
        "bug",
        "fire"
      ],
      "total": 2
    },
    {
      "_id": [
        "bug",
        "ghost"
      ],
      "total": 1
    },
    {
      "_id": [
        "dragon",
        "dark"
      ],
      "total": 1
    },
    {
      "_id": [
        "rock",
        "grass"
      ],
      "total": 1
    },
    {
      "_id": [
        "fighting",
        "psychic"
      ],
      "total": 4
    },
    {
      "_id": [
        "ground",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "water",
        "dark"
      ],
      "total": 4
    },
    {
      "_id": [
        "steel",
        "grass"
      ],
      "total": 2
    },
    {
      "_id": [
        "ghost"
      ],
      "total": 9
    },
    {
      "_id": [
        "ghost",
        "electric"
      ],
      "total": 1
    },
    {
      "_id": [
        "ice",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "rock",
        "steel"
      ],
      "total": 6
    },
    {
      "_id": [
        "grass",
        "psychic"
      ],
      "total": 3
    },
    {
      "_id": [
        "ground",
        "dragon"
      ],
      "total": 5
    },
    {
      "_id": [
        "normal"
      ],
      "total": 52
    },
    {
      "_id": [
        "flying",
        "grass"
      ],
      "total": 5
    },
    {
      "_id": [
        "ghost",
        "dark"
      ],
      "total": 2
    },
    {
      "_id": [
        "normal",
        "fire"
      ],
      "total": 1
    },
    {
      "_id": [
        "flying",
        "water"
      ],
      "total": 5
    },
    {
      "_id": [
        "fighting",
        "grass"
      ],
      "total": 2
    },
    {
      "_id": [
        "fighting",
        "fire"
      ],
      "total": 6
    },
    {
      "_id": [
        "normal",
        "fighting"
      ],
      "total": 1
    },
    {
      "_id": [
        "ground",
        "grass"
      ],
      "total": 1
    },
    {
      "_id": [
        "bug"
      ],
      "total": 14
    },
    {
      "_id": [
        "flying",
        "dragon"
      ],
      "total": 3
    },
    {
      "_id": [
        "flying",
        "fire"
      ],
      "total": 5
    },
    {
      "_id": [
        "ground",
        "fire"
      ],
      "total": 2
    },
    {
      "_id": [
        "ghost",
        "ice"
      ],
      "total": 1
    },
    {
      "_id": [
        "flying",
        "rock"
      ],
      "total": 4
    },
    {
      "_id": [
        "dragon",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "poison",
        "bug"
      ],
      "total": 10
    },
    {
      "_id": [
        "grass",
        "dark"
      ],
      "total": 3
    },
    {
      "_id": [
        "rock"
      ],
      "total": 7
    },
    {
      "_id": [
        "fire",
        "dark"
      ],
      "total": 3
    },
    {
      "_id": [
        "ground"
      ],
      "total": 10
    },
    {
      "_id": [
        "ice"
      ],
      "total": 4
    },
    {
      "_id": [
        "water",
        "fairy"
      ],
      "total": 2
    },
    {
      "_id": [
        "rock",
        "water"
      ],
      "total": 9
    },
    {
      "_id": [
        "poison",
        "water"
      ],
      "total": 3
    },
    {
      "_id": [
        "flying",
        "ice"
      ],
      "total": 2
    },
    {
      "_id": [
        "dark",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "fighting",
        "water"
      ],
      "total": 1
    },
    {
      "_id": [
        "grass"
      ],
      "total": 25
    },
    {
      "_id": [
        "fairy",
        "psychic"
      ],
      "total": 4
    },
    {
      "_id": [
        "normal",
        "fairy"
      ],
      "total": 4
    },
    {
      "_id": [
        "ground",
        "ice"
      ],
      "total": 3
    },
    {
      "_id": [
        "normal",
        "psychic"
      ],
      "total": 1
    },
    {
      "_id": [
        "bug",
        "electric"
      ],
      "total": 2
    },
    {
      "_id": [
        "ground",
        "bug"
      ],
      "total": 1
    },
    {
      "_id": [
        "ice",
        "dark"
      ],
      "total": 2
    },
    {
      "_id": [
        "steel",
        "dragon"
      ],
      "total": 1
    },
    {
      "_id": [
        "flying",
        "fairy"
      ],
      "total": 2
    },
    {
      "_id": [
        "dark"
      ],
      "total": 8
    },
    {
      "_id": [
        "bug",
        "steel"
      ],
      "total": 6
    },
    {
      "_id": [
        "ghost",
        "fire"
      ],
      "total": 2
    },
    {
      "_id": [
        "steel",
        "psychic"
      ],
      "total": 6
    },
    {
      "_id": [
        "rock",
        "fire"
      ],
      "total": 1
    },
    {
      "_id": [
        "poison",
        "ground"
      ],
      "total": 2
    },
    {
      "_id": [
        "bug",
        "water"
      ],
      "total": 1
    },
    {
      "_id": [
        "water",
        "ice"
      ],
      "total": 6
    },
    {
      "_id": [
        "ground",
        "water"
      ],
      "total": 9
    },
    {
      "_id": [
        "flying",
        "ghost"
      ],
      "total": 2
    },
    {
      "_id": [
        "fire",
        "dragon"
      ],
      "total": 1
    },
    {
      "_id": [
        "water",
        "dragon"
      ],
      "total": 1
    },
    {
      "_id": [
        "fairy"
      ],
      "total": 13
    },
    {
      "_id": [
        "water",
        "electric"
      ],
      "total": 3
    },
    {
      "_id": [
        "ghost",
        "grass"
      ],
      "total": 5
    },
    {
      "_id": [
        "water",
        "grass"
      ],
      "total": 3
    },
    {
      "_id": [
        "flying",
        "poison"
      ],
      "total": 3
    },
    {
      "_id": [
        "grass",
        "ice"
      ],
      "total": 3
    },
    {
      "_id": [
        "dragon"
      ],
      "total": 4
    },
    {
      "_id": [
        "steel"
      ],
      "total": 3
    },
    {
      "_id": [
        "fighting",
        "bug"
      ],
      "total": 2
    },
    {
      "_id": [
        "normal",
        "flying"
      ],
      "total": 19
    },
    {
      "_id": [
        "flying",
        "psychic"
      ],
      "total": 4
    },
    {
      "_id": [
        "electric"
      ],
      "total": 24
    },
    {
      "_id": [
        "fighting",
        "dark"
      ],
      "total": 2
    },
    {
      "_id": [
        "flying",
        "electric"
      ],
      "total": 4
    },
    {
      "_id": [
        "poison",
        "dark"
      ],
      "total": 3
    },
    {
      "_id": [
        "ground",
        "rock"
      ],
      "total": 9
    },
    {
      "_id": [
        "fire"
      ],
      "total": 23
    },
    {
      "_id": [
        "bug",
        "grass"
      ],
      "total": 5
    },
    {
      "_id": [
        "steel",
        "water"
      ],
      "total": 1
    },
    {
      "_id": [
        "poison",
        "ghost"
      ],
      "total": 3
    },
    {
      "_id": [
        "water"
      ],
      "total": 53
    },
    {
      "_id": [
        "rock",
        "bug"
      ],
      "total": 4
    },
    {
      "_id": [
        "water",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "ground",
        "dark"
      ],
      "total": 2
    },
    {
      "_id": [
        "flying",
        "ground"
      ],
      "total": 2
    },
    {
      "_id": [
        "ghost",
        "dragon"
      ],
      "total": 1
    },
    {
      "_id": [
        "electric",
        "ice"
      ],
      "total": 1
    },
    {
      "_id": [
        "poison",
        "grass"
      ],
      "total": 14
    },
    {
      "_id": [
        "steel",
        "electric"
      ],
      "total": 3
    },
    {
      "_id": [
        "psychic"
      ],
      "total": 27
    },
    {
      "_id": [
        "flying",
        "dark"
      ],
      "total": 3
    },
    {
      "_id": [
        "fighting"
      ],
      "total": 15
    },
    {
      "_id": [
        "poison"
      ],
      "total": 14
    },
    {
      "_id": [
        "rock",
        "psychic"
      ],
      "total": 2
    },
    {
      "_id": [
        "flying",
        "bug"
      ],
      "total": 13
    },
    {
      "_id": [
        "flying",
        "steel"
      ],
      "total": 1
    }
  ],
  "ok": 1
}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> 

# 6. Realizar 3 counts na pokemons
.count -- todos
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.count({})
610
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean>

.count -- só tipo fogo
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.count({'types': 'fire'})
47
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> 

.count -- só de quantos tem a defesa maior que 70
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> db.pokemons.count({'defense': {$gt:70}})
250
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean> 