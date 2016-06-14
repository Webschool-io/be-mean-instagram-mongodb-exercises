## MongoDb - Aula 05
Autor: Lucas Frutig

1. Importar as collections `restaurantes` e `pokemons`.
2. Distinct por `cuisine` na restaurantes.
3. Distinct por `types` na pokemons.
4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
5. Group ou Aggregate contando a quantidade de pokemons de cada tipo.
6. Realizar 3 counts na pokemons.
	-> .count -- todos
	-> .count -- só tipo fogo
	-> .count -- só de quantos tem a defesa maior que 70


## Estrutura


### Importar as collections `restaurantes` e `pokemons`.
**Importando Restaurantes**
```
lucas@vahalla:~/Cursos/MongoDB$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurante.json
2016-06-14T15:57:42.295-0300	connected to: 127.0.0.1
2016-06-14T15:57:42.303-0300	dropping: be-mean.restaurantes
2016-06-14T15:57:44.140-0300	imported 25359 documents
lucas@vahalla:~/Cursos/MongoDB$ 

```
**Importando Pokemons**
```
lucas@vahalla:~/Cursos/MongoDB$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2016-06-14T15:59:36.492-0300	connected to: 127.0.0.1
2016-06-14T15:59:36.493-0300	dropping: be-mean.pokemons
2016-06-14T15:59:36.765-0300	imported 610 documents


```
### Distinct por `cuisine` na restaurantes.
```
vahalla(mongod-3.2.7) be-mean> db.restaurantes.distinct('cuisine').sort()
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
vahalla(mongod-3.2.7) be-mean> db.pokemons.distinct('types').sort()
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
**Página 1**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.find().limit(5).skip(0)
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
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
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
Fetched 5 record(s) in 6ms
```

**Página 2**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.find().limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 5ms
```

**Página 3**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.find().limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 6ms

```

### Group ou Aggregate contando a quantidade de pokemons de cada tipo.

**Group**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(current,result){
... current.types.forEach(function(type){
... if(result[type]){
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... })
... }
... })
[
  {
    "total": 915,
    "fire": 47,
    "normal": 78,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "poison": 54,
    "psychic": 62,
    "fighting": 38,
    "ghost": 34,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]

```

**Aggregate**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.aggregate([
... { $unwind: '$types'},
... {
... $group: {
... _id: '$types',
... count: { $sum:1 }
... }
... }
... ])
{
  "waitedMS": NumberLong("0"),
  "result": [
    {
      "_id": "grass",
      "count": 75
    },
    {
      "_id": "ghost",
      "count": 34
    },
    {
      "_id": "fire",
      "count": 47
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
      "_id": "rock",
      "count": 46
    },
    {
      "_id": "water",
      "count": 105
    },
    {
      "_id": "flying",
      "count": 77
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
    },
    {
      "_id": "ice",
      "count": 24
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
    }
  ],
  "ok": 1
}

```

### Realizar 3 counts na pokemons.
**count todos**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.count({})
610

```
**count só do tipo fogo**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.count({types:'fire'})
47
```
**count de quantos tem a defesa maior que 70**
```
vahalla(mongod-3.2.7) be-mean> db.pokemons.count({defense: {$gt:70}})
250

```


