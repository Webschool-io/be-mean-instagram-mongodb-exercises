# MongoDB - Aula 05 - Exercício
```
autor: Ruy Outor
```


# 1. Importar as collections restaurantes e pokemons

```js
$ mongoimport --db be-mean --collection restaurantes --drop --file MongoDB/be-mean-instagram-mongodb/exercises/restaurantes.json 
2016-08-12T01:10:44.135+0000    connected to: localhost
2016-08-12T01:10:44.136+0000    dropping: be-mean.restaurantes
2016-08-12T01:10:45.779+0000    imported 25359 documents

mongoimport --db be-mean --collection pokemons --drop --file MongoDB/be-mean-instagram-mongodb/exercises/pokemons.json 
2016-08-12T01:11:24.897+0000    connected to: localhost
2016-08-12T01:11:24.897+0000    dropping: be-mean.pokemons
2016-08-12T01:11:24.916+0000    imported 610 documents
```

# 2. Distinct por `cuisine` na restaurantes.

```js
db.restaurantes.distinct('cuisine').sort()
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

# 3. Distinct por `types` na pokemons

```js
db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "flying",
  "normal",
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

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```js
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Charmander"
}
{
  "name": "Blastoise"
}
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Butterfree"
}
Fetched 5 record(s) in 0ms

db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Spearow"
}
{
  "name": "Rattata"
}
{
  "name": "Kakuna"
}
{
  "name": "Wartortle"
}
{
  "name": "Charmeleon"
}
Fetched 5 record(s) in 1ms

db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Farfetchd"
}
{
  "name": "Magneton"
}
{
  "name": "Doduo"
}
{
  "name": "Seel"
}
{
  "name": "Dodrio"
}
Fetched 5 record(s) in 1ms
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
db.pokemons.group({
    initial: {total: 0},
    reduce: function(curr, result){
        curr.types.forEach(function(type){
            if (result[type]){
                result[type]++;
            } else {
                result[type] = 1;
            }
            result.total++;
        });
    }
})
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "normal": 78,
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

# 6. Realizar 3 counts na pokemons.

```js
db.pokemons.count({})
610

db.pokemons.count({types: 'fire'})
47

db.pokemons.count({defense: {$gt: 70}})
250
```
