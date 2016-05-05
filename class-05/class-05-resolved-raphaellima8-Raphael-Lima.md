# MongoDB - Aula 05 - Exercício
autor: Raphael Lima

# 1. Importar a collection de restaurantes e pokemons;
```
mongoimport --host localhost --db be-mean --collection restaurantes --drop --file /var/www/html/be-mean-instagram/apostila/module-mongodb/data/restaurantes.json
2015-11-21T18:55:48.722-0200	connected to: localhost
2015-11-21T18:55:48.722-0200	dropping: be-mean.restaurantes
2015-11-21T18:55:49.738-0200	imported 25359 documents

mongoimport --host localhost --db be-mean --collection pokemons --drop --file /var/www/html/be-mean-instagram/apostila/module-mongodb/data/pokemons.json
2015-11-21T18:57:55.409-0200	connected to: localhost
2015-11-21T18:57:55.410-0200	dropping: be-mean.pokemons
2015-11-21T18:57:55.442-0200	imported 610 documents
```

---
# 2. distinct() por `cuisine` na restaurantes;
```
debian(mongod-3.0.7) be-mean> db.restaurantes.distinct("cuisine").sort()
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
---
# 3. distinct() por `type` na pokemons;
```
debian(mongod-3.0.7) be-mean> db.pokemons.distinct("types")
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

---
# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons de (5 em 5);
```
debian(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(5*1)
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  ]
}
Fetched 5 record(s) in 3ms

debian(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(5*2)
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.441502",
  "defense": 45,
  "height": "14",
  "hp": 35,
  "name": "Doduo",
  "speed": 75,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "attack": 110,
  "created": "2013-11-03T15:05:41.443720",
  "defense": 70,
  "height": "18",
  "hp": 60,
  "name": "Dodrio",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
Fetched 5 record(s) in 2ms

debian(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(5*3)
{
  "_id": ObjectId("564b1dae25337263280d0489"),
  "attack": 70,
  "created": "2013-11-03T15:05:41.447897",
  "defense": 80,
  "height": "17",
  "hp": 90,
  "name": "Dewgong",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048a"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.457865",
  "defense": 30,
  "height": "13",
  "hp": 30,
  "name": "Gastly",
  "speed": 80,
  "types": [
    "poison",
    "ghost"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048b"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.456387",
  "defense": 180,
  "height": "15",
  "hp": 50,
  "name": "Cloyster",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048c"),
  "attack": 105,
  "created": "2013-11-03T15:05:41.452237",
  "defense": 75,
  "height": "12",
  "hp": 105,
  "name": "Muk",
  "speed": 50,
  "types": [
    "poison"
  ]
}
Fetched 5 record(s) in 2ms
```
---
# 5. `group()` ou `aggregate()` contando a quantidade de pokemons de cada tipo;
```
debian(mongod-3.0.7) be-mean> db.pokemons.group({
...   initial:{total: 0},
...   reduce:function(current, result){
...     current.types.forEach(function(type){
...         if(result[type]){
...           result[type]++;
...         } else{
...           result[type] = 1;
...         }
...         result.total++;
...       });
...   }
...   });
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
```

---

# 6. Realizar 3 count() na pokemons.
### 6.1 .count() -- todos;
```
debian(mongod-3.0.7) be-mean> db.pokemons.count()
610
```

### 6.2 .count() -- tipo fogo;
```
debian(mongod-3.0.7) be-mean> db.pokemons.count({types: "fire"})
47
```

### 6.3 .count() -- defesa maior que 70.
```
debian(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```
---
