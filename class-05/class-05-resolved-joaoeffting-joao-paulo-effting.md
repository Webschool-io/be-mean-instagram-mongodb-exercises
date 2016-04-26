## 1. Importar as collections restaurantes e pokemons.

``` 
mongoimport --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
2016-04-12T21:50:10.587-0300 dropping: be-mean-instagram.restaurantes
2016-04-12T21:50:12.309-0300 check 9 25359
2016-04-12T21:50:12.326-0300 imported 25359 objects

mongoimport --db be-mean-pokemons --collection pokemons --drop --file pokemons.json

mongoimport --db be-mean-pokemons --collection pokemons --drop --file pokemons.json
connected to: 127.0.0.1
2016-04-12T21:50:43.793-0300 dropping: be-mean-pokemons.pokemons
2016-04-12T21:50:43.833-0300 check 9 610
2016-04-12T21:50:43.835-0300 imported 610 objects
```

## 2. Distinct por `cuisine` na restaurantes.
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

## 3-  Distinct por types na pokemons.
``` 
db.pokemons.distinct("types")
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
db.pokemons.find({},{name:1}).limit(5).skip(5*0)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "name": "Rattata"
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "name": "Charmander"
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "name": "Charmeleon"
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "name": "Wartortle"
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "name": "Blastoise"
}
Fetched 5 record(s) in 15ms
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({},{name:1}).limit(5).skip(5*1)
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "name": "Caterpie"
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "name": "Metapod"
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "name": "Butterfree"
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "name": "Spearow"
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "name": "Kakuna"
}
Fetched 5 record(s) in 2ms
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({},{name:1}).limit(5).skip(5*2)
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "name": "Farfetchd"
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "name": "Magnemite"
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "name": "Magneton"
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "name": "Doduo"
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "name": "Seel"
}
Fetched 5 record(s) in 2ms

```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.group({
... initial: {total: 0},
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
db.pokemons.count({types:'ghost'})
34

db.pokemons.count({attack:{$gte: 100}})
126

db.pokemons.count({$and:[{attack:{$gte: 100}},{defense:{$gte:100}}]})
45

```
