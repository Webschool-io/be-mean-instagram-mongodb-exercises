#MongoDB - Aula 05 - Exercícios
autor: Douglas Zuqueto

##1. Importar as collections restaurantes e pokemons
### 1.1 Restaurantes
```
[dzuqueto@fedora WebSchool]$  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-25T00:38:06.295-0200	connected to: localhost
2015-11-25T00:38:06.295-0200	dropping: be-mean.restaurantes
2015-11-25T00:38:07.316-0200	imported 25359 documents

```
### 1.2 Pokemons
```
[dzuqueto@fedora WebSchool]$  mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-25T00:38:49.985-0200	connected to: localhost
2015-11-25T00:38:49.985-0200	dropping: be-mean.pokemons
2015-11-25T00:38:49.995-0200	imported 610 documents

```

##2. Distinct por `cuisine` na restaurantes
```javascript
fedora(mongod-3.0.4) be-mean> db.restaurantes.distinct('cuisine').sort()
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

##3. Distinct por `types` na pokemons
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.distinct('types').sort()
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

##4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)
### 4.1 Página 0
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*0)
{
  "name": "Charmeleon"
}
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Wartortle"
}
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 0ms
```
### 4.2 Página 1
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*1)
{
  "name": "Blastoise"
}
{
  "name": "Metapod"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 1ms

```
### 4.3 Página 2
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*2)
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
  "name": "Dodrio"
}
Fetched 5 record(s) in 1ms

```
##5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
### 5.1 Group
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type){
... if (result[type]){
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
    "fire": 47,
    "normal": 78,
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
### 5.2 Aggregate
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.aggregate([
... { $unwind: '$types' },
... { $group: {
... _id: '$types',
... count: {$sum: 1}
... }
... }
... ])
{
  "result": [
    {
      "_id": "fairy",
      "count": 28
    },
    {
      "_id": "psychic",
      "count": 62
    },
    {
      "_id": "fighting",
      "count": 38
    },
    {
      "_id": "dark",
      "count": 38
    },
    {
      "_id": "ground",
      "count": 51
    },
    {
      "_id": "grass",
      "count": 75
    },
    {
      "_id": "electric",
      "count": 40
    },
    {
      "_id": "steel",
      "count": 37
    },
    {
      "_id": "rock",
      "count": 46
    },
    {
      "_id": "flying",
      "count": 77
    },
    {
      "_id": "fire",
      "count": 47
    },
    {
      "_id": "ice",
      "count": 24
    },
    {
      "_id": "bug",
      "count": 61
    },
    {
      "_id": "poison",
      "count": 54
    },
    {
      "_id": "ghost",
      "count": 34
    },
    {
      "_id": "dragon",
      "count": 20
    },
    {
      "_id": "water",
      "count": 105
    },
    {
      "_id": "normal",
      "count": 78
    }
  ],
  "ok": 1
}

```

##6. Realizar 3 counts na pokemons.
### 6.1 Todos
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.count()
610
```

### 6.2 Somente do Tipo 'fire'
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.count({types:{$in:['fire']}})
47
```
### 6.3 Defesa menor ou igual 50 OU hp menor ou igual 40
```javascript
fedora(mongod-3.0.4) be-mean> db.pokemons.count({$or:[{defense:{$lte:50}},{hp:{$lte:40}}]})
202

```
