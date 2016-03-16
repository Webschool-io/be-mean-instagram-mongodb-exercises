# MongoDB - Aula 05 - Exercício
autor: Sóstenes Freitas de Andrade usuario:(sostenesfreitas)
## 1. Importar as collections restaurantes e pokemons.

```
BlackArch(mongod-3.2.1) be-mean> mongoimport --host 127.0.0.1 -db be-mean -collection restaurantes --drop --file restaurantes.json 
2016-02-10T09:25:54.025-0200    connected to: localhost
2016-02-10T09:25:54.025-0200    dropping: be-mean.restaurantes
2016-02-10T09:25:54.728-0200    imported 25359 documents

BlackArch(mongod-3.2.1) be-mean> mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
connected to: 127.0.0.1
2015-11-27T13:09:03.868-0300 dropping: be-mean.pokemons
2015-11-27T13:09:04.123-0300 check 9 610
2015-11-27T13:09:04.124-0300 imported 610 objects

```

## 2. Distinct por `cuisine` em restaurantes
```
BlackArch(mongod-3.2.1) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "American ",
  "Jewish/Kosher",
  "Irish",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
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
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Polish",
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
  "Polynesia",                                                                                                     "Australian",
  "Hotdogs/Pretzels",
  "Southwestern",
  "Nuts/Confectionary",
  "Hawaiian",
  "Creole/Cajun",
  "Californian",
  "Chilean"
]
```

## 3. Distinct por `types` em pokemons
```
BlackArch(mongod-3.2.1) be-mean> db.pokemons.distinct('types')
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
```
## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5em 5)
```
BlackArch(mongod-3.2.1) be-mean> db.pokemons.find().limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 2ms
BlackArch(mongod-3.2.1) be-mean> db.pokemons.find().limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 2ms
BlackArch(mongod-3.2.1) be-mean> db.pokemons.find().limit(5).skip(5 * 3)
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
Fetched 5 record(s) in 1ms
```
#5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
be-mean> db.pokemons.group({ 
                              initial: {total: 0}, reduce:function(curr, result){                    
                                      curr.types.forEach(function(type){ if (result[type])
                                           {  result[type]++;
                                            }else{ 
                                                  result[type] = 1; 
                                            } result.total++; }); } });
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
```
# 6.Realizar 3 counts na pokemons
```
BlackArch(mongod-3.2.1) be-mean> db.pokemons.count({})
610
BlackArch(mongod-3.2.1) be-mean> db.pokemons.count({'types':'fire'})
47
BlackArch(mongod-3.2.1) be-mean> db.pokemons.count({'defense':{$gt:70}})
250
```
