# MongoDB - Aula 05 - Exercício
autor: **Sergio Diniz Correia**

# 1- Importar as collections restaurantes e pokemons.
```javascript
Sergios-MacBook-Pro:~ sergiodiniz$ mongoimport --db be-mean --collection pokemons --drop --file ../../Volumes/Arquivos/Sergio/Documentos/Estudos/be-mean/MongoDB/aula5/pokemons.json 
2016-01-22T07:29:41.996-0300  connected to: localhost
2016-01-22T07:29:41.997-0300  dropping: be-mean.pokemons
2016-01-22T07:29:42.019-0300  imported 610 documents

Sergios-MacBook-Pro:~ sergiodiniz$ mongoimport --db be-mean --collection restaurantes --drop --file ../../Volumes/Arquivos/Sergio/Documentos/Estudos/be-mean/MongoDB/aula5/restaurantes.json 
2016-01-22T07:30:12.503-0300  connected to: localhost
2016-01-22T07:30:12.503-0300  dropping: be-mean.restaurantes
2016-01-22T07:30:13.966-0300  imported 25359 documents
})

show collections
pokemons       →  0.140MB /  0.164MB
restaurantes   → 14.012MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 
```

# 2- Distinct por cuisine na restaurantes.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Irish",
  "Hamburgers",
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 
})


```

# 3- Distinct por types na pokemons.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "water",
  "fire",
  "bug",
  "flying",
  "normal",
  "poison",
  "electric",
  "steel",
  "ghost",
  "ice",
  "psychic",
  "fighting",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```

# 4- As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```javascript
//primeira pagina
db.pokemons.find().limit(5).skip(5 * 0)
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
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
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ]
}
Fetched 5 record(s) in 4ms
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


// Segunda Pagina
db.pokemons.find().limit(5).skip(5 * 1)
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


// Terceira Pagina
db.pokemons.find().limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 6ms
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 
```

# 5- Group ou Aggregate contando a quantidade de pokemons de cada tipo
```javascript
db.pokemons.group({
...   initial: {count: 0},
...   reduce: function(curr, result) {
...     curr.types.forEach(function(property) {
...       if(result[property])
...         result[property]++;
...       else
...         result[property] = 1;
... 
...       result.count++;
...     })
...   }
... })
[
  {
    "count": 915,
    "water": 105,
    "fire": 47,
    "bug": 61,
    "flying": 77,
    "normal": 78,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ghost": 34,
    "ice": 24,
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```

# 6- Realizar 3 counts na pokemons.
```javascript
// Primeiro
db.pokemons.count()
610
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 

// Segundo
 db.pokemons.count({types : 'dragon'})
20
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 

// Terceiro
db.pokemons.count({speed: {$gt: 70}})
230
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 

```
