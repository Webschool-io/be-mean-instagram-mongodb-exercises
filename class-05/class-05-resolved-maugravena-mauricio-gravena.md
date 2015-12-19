# MongoDB - Aula 05 - Exercício
Autor: Mauricio Gravena de Oliveira

## 1. Importar as collections restaurantes e pokemons
```
➜  ~  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
➜  ~  mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
```

## 2. Distinct por `cuisine` na restaurantes
```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "American ",
  "Bakery",
  "Jewish/Kosher",
  "Delicatessen",
  "Chinese",
  "Irish",
  "Ice Cream, Gelato, Yogurt, Ices",
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
  "Greek",
  "Not Listed/Not Applicable",
  "Hotdogs",
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

## 3. Distinct por `types` na pokemons
```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.distinct('types')
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
{
  "name": "Metapod"
}
{
  "name": "Wartortle"
}
Fetched 5 record(s) in 2ms
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
Fetched 5 record(s) in 4ms
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
{
  "name": "Dewgong"
}
Fetched 5 record(s) in 3ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.group({
...   initial: {total: 0},
...   reduce: function(curr, result) {
...     curr.types.forEach(function(type) {
...       if (result [type]) {
...         result[type]++;
...       } else {
...         result[type] = 1;
...       }
...       result.total++;  
...     });
...   }
... });
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "normal": 78,
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

## 6. Realizar 3 counts na pokemons.

### -> .count -- todos

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.count()
610
```
### -> .count -- só tipo fogo

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.count({types: 'fire'})
47
```
### -> .count -- só de quantos tem a defesa maior que 70

```
mau(mongod-3.2.0-rc3-110-g327660f) be-mean> db.pokemons.count({defense: {$lt: 70}})
315
```
