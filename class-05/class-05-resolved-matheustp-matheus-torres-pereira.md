# MongoDB - Aula 05 - Exercício
autor: Matheus Torres Pereira

## 1. Importar as collections restaurantes e pokemons.

```
matt@ubuntu ~/mongodb> mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
2017-02-24T16:12:45.538-0300	connected to: 127.0.0.1
2017-02-24T16:12:45.538-0300	dropping: be-mean.restaurantes
2017-02-24T16:12:47.364-0300	imported 25359 documents

matt@ubuntu ~/mongodb> mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection novospokemons --drop --file pokemons.json
2017-02-24T16:12:19.463-0300	connected to: 127.0.0.1
2017-02-24T16:12:19.464-0300	dropping: be-mean-pokemons.novospokemons
2017-02-24T16:12:19.508-0300	imported 610 documents
```

## 2. Distinct por cuisine na restaurantes.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.distinct('cuisine')
[
  "American ",
  "Jewish/Kosher",
  "Irish",
  "Bakery",
  "Delicatessen",
  "Chinese",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chicken",
  "Turkish",
  "Hamburgers",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Pizza",
  "Continental",
  "Steak",
  "Italian",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "German",
  "French",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Soul Food",
  "Pancakes/Waffles",
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
```

## 3. Distinct por types na pokemons.

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.distinct('types')
[
  "water",
  "bug",
  "flying",
  "normal",
  "poison",
  "electric",
  "steel",
  "fire",
  "ghost",
  "ice",
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

## 4.As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.find().limit(5).skip(5*0)
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
Fetched 5 record(s) in 9ms
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.find().limit(5).skip(5*1)
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
Fetched 5 record(s) in 6ms
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.find().limit(5).skip(5*2)
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
Fetched 5 record(s) in 3ms
```

## 5.Group ou Aggregate contando a quantidade de pokemons de cada tipo.

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.group({
... initial: {total : 0},
... reduce: function (curr, result){
... curr.types.forEach(function (type){
... if (result[type]){
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... })
... }
... });
[
  {
    "total": 915,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "normal": 78,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "fire": 47,
    "ghost": 34,
    "ice": 24,
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

## 6. Realizar 3 counts na pokemons.
```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.count({types: 'fire'})
47

ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.count({attack: {$gt: 50}})
462

ubuntu(mongod-3.2.12) be-mean-pokemons> db.novospokemons.count({$and: [{attack: {$gt: 50}}, {types: 'fire'}]})
40

```