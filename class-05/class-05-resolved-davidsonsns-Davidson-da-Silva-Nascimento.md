# MongoDB - Aula 05 - Exercício
**autor:** Davidson da Silva Nascimento
## 1. Importar as collections restaurantes e pokemons
```js
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Desktop/restaurantes.json
2015-12-01T18:17:21.490-0200    connected to: 127.0.0.1
2015-12-01T18:17:21.494-0200    dropping: be-mean.restaurantes
2015-12-01T18:17:23.247-0200    imported 25359 documents

mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Desktop/pokemons.json
2015-12-01T18:18:34.695-0200    connected to: 127.0.0.1
2015-12-01T18:18:34.696-0200    dropping: be-mean.pokemons
2015-12-01T18:18:34.716-0200    imported 610 documents
```
## 2. Distinct por `cuisine` na restaurantes
#### Não foi solicitado, porém foi inserido sort() pra ordenar
```js
> db.restaurantes.distinct('cuisine').sort()
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
## 3. Distinct por `types` na pokemons
#### Não foi solicitado, porém foi inserido sort() pra ordenar
```js
> db.pokemons.distinct('types').sort()
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
## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```js
> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0).pretty()
{ "name" : "Charmander" }
{ "name" : "Charmeleon" }
{ "name" : "Rattata" }
{ "name" : "Blastoise" }
{ "name" : "Wartortle" }

> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1).pretty()
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2).pretty()
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
```
## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
> db.pokemons.group({
...    initial: {},
...    reduce: function(current, result) {
...      current.types.forEach(function(type) {
...        if (result[type]) {
...          result[type]++;
...        } else {
...          result[type] = 1;
...        }
...      });
...    }
... });
[
        {
                "fire" : 47,
                "normal" : 78,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "ghost" : 34,
                "ice" : 24,
                "fighting" : 38,
                "psychic" : 62,
                "grass" : 75,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }
]
```
## 6. Realizar 3 counts na pokemons
```js
> db.pokemons.count({types: 'fire', attack: {$gt: 100}})
9

> db.pokemons.count({types: {$in: [/ice/i, /fire/i]}, attack: {$lt: 50}})
7

> db.pokemons.count({types: {$not: /fire/i}})
563
```