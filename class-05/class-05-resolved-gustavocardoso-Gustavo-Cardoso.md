# MongoDB - Aula 05 - Exercício
autor: Gustavo Cardoso

## Importar as collections restaurantes e pokemons

```
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-12-10T16:33:53.171-0200  connected to: 127.0.0.1
2015-12-10T16:33:53.172-0200  dropping: be-mean.pokemons
2015-12-10T16:33:53.361-0200  imported 610 documents

$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-10T16:34:32.210-0200  connected to: 127.0.0.1
2015-12-10T16:34:32.211-0200  dropping: be-mean.restaurantes
2015-12-10T16:34:33.266-0200  imported 25359 documents
```

## Distinct por "cuisine" na restaurantes

```
db.restaurantes.distinct('cuisine');
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
  "Donuts",
  "Caribbean",
  "Sandwiches/Salads/Mixed Buffet",
  "Continental",
  "Pizza",
  "Bagels/Pretzels",
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

## Distinct por "types" na pokemons

```
db.pokemons.distinct('types');
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

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(1 * 5);
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
{
  "name": "Wartortle"
}
Fetched 5 record(s) in 2ms


db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(2 * 5);
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
  "name": "Seel"
}
Fetched 5 record(s) in 2ms


db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(3 * 5);
{
  "name": "Dodrio"
}
{
  "name": "Dewgong"
}
{
  "name": "Gastly"
}
{
  "name": "Poliwag"
}
{
  "name": "Cloyster"
}
Fetched 5 record(s) in 3ms
```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.group({
...   initial: { total: 0 },
...   reduce: function(current, result) {
...     current.types.forEach(function(type) {
...       if(result[type]) {
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