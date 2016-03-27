# MongoDB - Aula 05 - Exercício
**Autor**: Josimar Zimermann - [josimarz](https://github.com/josimarz)

## 1. Importar a coleção `pokemons`

```js
mongoimport --db be-mean --collection pokemons --drop --file ~/Downloads/pokemons.json 
2016-02-22T22:55:45.163-0300    connected to: localhost
2016-02-22T22:55:45.163-0300    dropping: be-mean.pokemons
2016-02-22T22:55:45.208-0300    imported 610 documents
```

## 2. Aplicar `distinct` sobre a propriedade `cuisine` da coleção `restaurantes`

```js
db.restaurantes.distinct('cuisine')
[
  "American ",
  "Irish",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Hamburgers",
  "Bakery",
  "Delicatessen",
  "Chinese",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Chicken",
  "Italian",
  "Steak",
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
  "African",
  "Not Listed/Not Applicable",
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

## 3. Aplicar `distinct` sobre a propriedade `types` na coleção `pokemons`

```js
db.pokemons.distinct('types')
[
  "fire",
  "normal",
  "water",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ghost",
  "fighting",
  "ice",
  "psychic",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
```

## 4. Apresentar as três (3) primeiras páginas da coleção `pokemons`, de 5 em 5, usando `limit` e `skip`

```js
db.pokemons.find().limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 3ms
db.pokemons.find().limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 3ms
db.pokemons.find().limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 3ms
db.pokemons.find().limit(5).skip(5 * 3)
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
{
  "_id": ObjectId("564b1daf25337263280d048d"),
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
  "_id": ObjectId("564b1daf25337263280d048e"),
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
Fetched 5 record(s) in 3ms
db.pokemons.find().limit(5).skip(5 * 4)
{
  "_id": ObjectId("564b1daf25337263280d048f"),
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
  "_id": ObjectId("564b1daf25337263280d0490"),
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
  "_id": ObjectId("564b1daf25337263280d0493"),
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
  "_id": ObjectId("564b1daf25337263280d0491"),
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
Fetched 5 record(s) in 3ms
```

## 5. Usar a função `group` ou `aggregate` para contabilizar o total de Pokemon de cada tipo distinto

```js
db.pokemons.aggregate([
... { $project: { _id: 0, types: 1 } },
... { $unwind: "$types" },
... { $group: { _id: "$types", total: { $sum: 1 } } },
... { $project: { _id: 0, type: "$_id", total: 1 } }
... ])
{
  "waitedMS": NumberLong("0"),
  "result": [
    {
      "total": 75,
      "type": "grass"
    },
    {
      "total": 38,
      "type": "dark"
    },
    {
      "total": 28,
      "type": "fairy"
    },
    {
      "total": 62,
      "type": "psychic"
    },
    {
      "total": 40,
      "type": "electric"
    },
    {
      "total": 20,
      "type": "dragon"
    },
    {
      "total": 61,
      "type": "bug"
    },
    {
      "total": 37,
      "type": "steel"
    },
    {
      "total": 24,
      "type": "ice"
    },
    {
      "total": 51,
      "type": "ground"
    },
    {
      "total": 54,
      "type": "poison"
    },
    {
      "total": 34,
      "type": "ghost"
    },
    {
      "total": 78,
      "type": "normal"
    },
    {
      "total": 38,
      "type": "fighting"
    },
    {
      "total": 46,
      "type": "rock"
    },
    {
      "total": 105,
      "type": "water"
    },
    {
      "total": 77,
      "type": "flying"
    },
    {
      "total": 47,
      "type": "fire"
    }
  ],
  "ok": 1
}
```

## 6. Realizar três operações `count` na coleção `pokemons`

### 6.1 Todos os registros na coleção `pokemons`

```js
db.pokemons.count()
610
```

### 6.2 Total de registros de Pokemon do tipo `fire`

```js
db.pokemons.count({types: /fire/i})
47
```

### 6.3 Total de registros de Pokemon cujo defese é maior que 70

```js
db.pokemons.count({defense: {$gt: 70}})
250
```