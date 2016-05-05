# MongoDB - Aula 05 - Exercício
autor: Rafael Taro Osako

##1. Importar as collections restaurantes e pokemons
```js
MacBook-Pro:desktop rafaeltaro$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-21T22:08:59.694-0200	connected to: 127.0.0.1
2015-12-21T22:08:59.694-0200	dropping: be-mean.restaurantes
2015-12-21T22:09:00.566-0200	imported 25359 documents


MacBook-Pro:desktop rafaeltaro$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-12-21T22:09:59.992-0200	connected to: 127.0.0.1
2015-12-21T22:09:59.993-0200	dropping: be-mean.pokemons
2015-12-21T22:10:00.007-0200	imported 610 documents
```

##2. Distinct por 'cuisine na restaurantes
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "American ",
  "Jewish/Kosher",
  "Bakery",
  "Hamburgers",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Irish",
  "Chinese",
  "Other",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Sandwiches/Salads/Mixed Buffet",
  "Continental",
  "Donuts",
  "Pizza",
  "Italian",
  "Bagels/Pretzels",
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

##3. Distinct por `types` na pokemons
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "normal",
  "bug",
  "water",
  "flying",
  "fire",
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

##4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*0)
{
  "name": "Rattata"
}
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 1ms

MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*1)
{
  "name": "Butterfree"
}
{
  "name": "Charmeleon"
}
{
  "name": "Spearow"
}
{
  "name": "Farfetchd"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 1ms

MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*2)
{
  "name": "Charmander"
}
{
  "name": "Magneton"
}
{
  "name": "Doduo"
}
{
  "name": "Magnemite"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 1ms
```

##5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.group( {
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if(result[type]) {
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
    "normal": 78,
    "bug": 61,
    "water": 105,
    "flying": 77,
    "fire": 47,
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

##6. Realizar 3 counts na pokemons.

* Todos:
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.count()
610
```


* Só do types == fire:
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.count({types:'fire'})
47
```

* Só com defense > 70:
```js
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.count({defense:{$gt:70}})
250
```