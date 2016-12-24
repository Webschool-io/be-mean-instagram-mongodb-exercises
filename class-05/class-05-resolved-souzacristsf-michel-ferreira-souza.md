# MongoDB - Aula 05 - Exercício
autor: [Michel Ferreira Souza](https://github.com/souzacristsf)

## 1. Importar as collections restaurantes e pokemons

```
michel@Souza:~$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Documentos/pokemons.json
2015-12-23T19:04:07.642-0200	connected to: 127.0.0.1
2015-12-23T19:04:07.643-0200	dropping: be-mean.pokemons
2015-12-23T19:04:07.718-0200	imported 620 documents

```

## 2. Distinct por cuisine na restaurantes

```
Souza(mongod-3.0.8) be-mean> db.restaurantes.distinct('cuisine')
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

## 3. Distinct por types na pokemons

```
Souza(mongod-3.0.8) be-mean> db.pokemons.distinct('types')
[
  "flying",
  "normal",
  "bug",
  "poison",
  "electric",
  "water",
  "psychic",
  "fighting",
  "grass",
  "fairy",
  "rock",
  "ice",
  "fire",
  "ground",
  "ghost",
  "dark",
  "steel",
  "dragon"
]

```

## 4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)

# Page 1

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Pidgeotto"
}
{
  "name": "Pidgeot"
}
{
  "name": "Fearow"
}
{
  "name": "Beedrill"
}
{
  "name": "Pidgey"
}
Fetched 5 record(s) in 2ms

```

# Page 2

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Pikachu"
}
{
  "name": "Arbok"
}
{
  "name": "Ekans"
}
{
  "name": "Raichu"
}
{
  "name": "Raticate"
}
Fetched 5 record(s) in 2ms

```

# Page 3

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Poliwag"
}
{
  "name": "Poliwhirl"
}
{
  "name": "Kadabra"
}
{
  "name": "Machop"
}
{
  "name": "Kangaskhan"
}
Fetched 5 record(s) in 3ms

```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

# Group 

```
Souza(mongod-3.0.8) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr,result){
...          curr.types.forEach(function(type){
...              if (result[type]){
...                  result[type]++;
...              }else{
...                  result[type]=1;
...              }
...              result.total++;
...          });
...      }
... });
[
  {
    "total": 934,
    "normal": 79,
    "flying": 81,
    "poison": 54,
    "bug": 58,
    "electric": 47,
    "water": 101,
    "psychic": 61,
    "fighting": 42,
    "grass": 70,
    "fairy": 31,
    "rock": 42,
    "ice": 28,
    "fire": 53,
    "ground": 53,
    "ghost": 34,
    "dark": 35,
    "steel": 35,
    "dragon": 30
  }
]

```

# Aggregate

```
Souza(mongod-3.0.8) be-mean> db.pokemons.aggregate([
... {$unwind: '$types'},
... {
... $group: {
... _id: '$types',
... types: {$sum: 1}
... 
... }
... }
... ])
{
  "result": [
    {
      "_id": "steel",
      "types": 35
    },
    {
      "_id": "ghost",
      "types": 34
    },
    {
      "_id": "ice",
      "types": 28
    },
    {
      "_id": "fire",
      "types": 53
    },
    {
      "_id": "dark",
      "types": 35
    },
    {
      "_id": "ground",
      "types": 53
    },
    {
      "_id": "electric",
      "types": 47
    },
    {
      "_id": "grass",
      "types": 70
    },
    {
      "_id": "psychic",
      "types": 61
    },
    {
      "_id": "fairy",
      "types": 31
    },
    {
      "_id": "fighting",
      "types": 42
    },
    {
      "_id": "poison",
      "types": 54
    },
    {
      "_id": "bug",
      "types": 58
    },
    {
      "_id": "dragon",
      "types": 30
    },
    {
      "_id": "water",
      "types": 101
    },
    {
      "_id": "rock",
      "types": 42
    },
    {
      "_id": "flying",
      "types": 81
    },
    {
      "_id": "normal",
      "types": 79
    }
  ],
  "ok": 1
}

```

## 6. Realizar 3 counts na pokemons.

```
Souza(mongod-3.0.8) be-mean> db.pokemons.count()
620
Souza(mongod-3.0.8) be-mean> db.pokemons.count({types: 'ice'})
28
Souza(mongod-3.0.8) be-mean> db.pokemons.count({defense:{$lte: 78}})
395

```
