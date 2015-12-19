# MongoDB - Aula 05 - Exercício
autor: Franklin Dias


## Importar as collections restaurantes e pokemons ##

```
[franklin.dias@localhost be-mean-instagram-atividades]$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json connected to: 127.0.0.1
2015-11-25T23:02:01.591-0200 dropping: be-mean.pokemons
2015-11-25T23:02:01.609-0200 check 9 610
2015-11-25T23:02:01.609-0200 imported 610 objects

[franklin.dias@localhost be-mean-instagram-atividades]$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
2015-11-24T23:03:11.121-0200 dropping: be-mean.restaurantes
2015-11-24T23:03:11.727-0200 check 9 25359
2015-11-24T23:03:11.754-0200 imported 25359 objects

```

## Distinct por cuisine na restaurantes ##

```javascript
localhost(mongod-2.6.11) be-mean> db.restaurantes.distinct('cuisine').sort()
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

## Distinct por types na pokemons ##

```javascript
localhost(mongod-2.6.11) be-mean> db.pokemons.distinct('types').sort()
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

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5) ##

#### Página 1

```javascript
localhost(mongod-2.6.11) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Ninetales"
}
{
  "name": "Wigglytuff"
}
{
  "name": "Zubat"
}
{
  "name": "Venonat"
}
{
  "name": "Meowth"
}
Fetched 5 record(s) in 20ms
```

#### Página 2

```javascript
localhost(mongod-2.6.11) be-mean>  db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Golbat"
}
{
  "name": "Oddish"
}
{
  "name": "Gloom"
}
{
  "name": "Vileplume"
}
{
  "name": "Paras"
}
Fetched 5 record(s) in 1ms
```

#### Página 3

```javascript
localhost(mongod-2.6.11) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Beedrill"
}
{
  "name": "Pidgey"
}
{
  "name": "Pidgeotto"
}
{
  "name": "Pidgeot"
}
{
  "name": "Raticate"
}
Fetched 5 record(s) in 4ms
```


## Group ou Aggregate contando a quantidade de pokemons de cada tipo ##

```javascript
localhost(mongod-2.6.11) be-mean> db.pokemons.group({
 ... initial: { total: 0 },
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
    "total": 1168,
    "fire": 62,
    "normal": 99,
    "fairy": 36,
    "flying": 98,
    "poison": 61,
    "bug": 71,
    "grass": 94,
    "electric": 50,
    "ground": 63,
    "water": 123,
    "fighting": 51,
    "psychic": 83,
    "rock": 56,
    "steel": 47,
    "ice": 38,
    "ghost": 44,
    "dragon": 44,
    "dark": 48
  }
]

```


## Realizar 3 counts na pokemons. ##
*-> .count -- todos -> .count -- só tipo fogo -> .count -- só de quantos tem a defesa maior que 70*

```javascript
localhost(mongod-2.6.11) be-mean> db.pokemons.count({})
778

localhost(mongod-2.6.11) be-mean> db.pokemons.count({'types': 'fire'})
62

localhost(mongod-2.6.11) be-mean> db.pokemons.count({'defense': {$gt: 70}})
340
```

