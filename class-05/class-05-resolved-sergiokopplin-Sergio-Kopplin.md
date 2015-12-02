## 1. Importar as collections restaurantes e pokemons

```
~ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-30T22:14:04.435-0200	connected to: 127.0.0.1
2015-11-30T22:14:04.436-0200	dropping: be-mean.restaurantes
2015-11-30T22:14:05.423-0200	imported 25359 documents

~ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons-full.json
2015-11-30T22:14:43.757-0200	connected to: 127.0.0.1
2015-11-30T22:14:43.757-0200	dropping: be-mean.pokemons
2015-11-30T22:14:43.779-0200	imported 620 documents
```

## 2. Distinct por `cuisine` na restaurantes
```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.restaurantes.distinct( 'cuisine' )
[
  "Bakery",
  "American ",
  "Irish",
  "Jewish/Kosher",
  "Hamburgers",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
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
  "German",
  "French",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Hotdogs",
  "Not Listed/Not Applicable",
  "African",
  "Greek",
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.distinct( 'types' )
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 0)
{
  "_id": ObjectId("564a7c362c153ed825a69054"),
  "attack": 90,
  "created": "2013-11-03T15:05:41.297180",
  "defense": 40,
  "height": "10",
  "hp": 65,
  "name": "Beedrill",
  "speed": 75,
  "types": [
    "poison",
    "bug"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69056"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.301609",
  "defense": 55,
  "height": "11",
  "hp": 63,
  "name": "Pidgeotto",
  "speed": 71,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69055"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.299457",
  "defense": 40,
  "height": "3",
  "hp": 40,
  "name": "Pidgey",
  "speed": 56,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69057"),
  "attack": 80,
  "created": "2013-11-03T15:05:41.303569",
  "defense": 75,
  "height": "15",
  "hp": 83,
  "name": "Pidgeot",
  "speed": 101,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564a7c362c153ed825a69058"),
  "attack": 81,
  "created": "2013-11-03T15:05:41.308092",
  "defense": 60,
  "height": "7",
  "hp": 55,
  "name": "Raticate",
  "speed": 97,
  "types": [
    "normal"
  ]
}
Fetched 5 record(s) in 4ms

Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 5ms

Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 6ms
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

Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.group({
    initial: { total: 0 },
    reduce: function(curr, result) {
        curr.types.forEach(function(type){
            if (result[type]) {
                result[type]++;
            } else {
                result[type] = 1;
            }
            result.total++;
        });
    }
});

# result
[
  {
    "total": 934,
    "poison": 54,
    "bug": 58,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "water": 101,
    "fighting": 42,
    "psychic": 61,
    "grass": 70,
    "fairy": 31,
    "fire": 53,
    "rock": 42,
    "ice": 28,
    "ground": 53,
    "steel": 35,
    "ghost": 34,
    "dark": 35,
    "dragon": 30
  }
]
```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find().count()
620
```

-> .count -- só tipo fogo

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({ types: 'fire' }).count()
53
```

-> .count -- só de quantos tem a defesa maior que 70

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({ defense: { $gt: 70 } }).count()
263
```
