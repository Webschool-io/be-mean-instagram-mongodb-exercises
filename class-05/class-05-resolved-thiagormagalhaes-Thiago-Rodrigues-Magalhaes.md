# MongoDB - Aula 05 - Exercício
autor: Thiago Rodrigues Magalhães

## Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-24T10:27:05.776-0300  connected to: 127.0.0.1
2015-11-24T10:27:05.777-0300  dropping: be-mean.restaurantes
2015-11-24T10:27:08.773-0300  [####################....] be-mean.restaurantes9.8 MB/11.3 MB (86.3%)
2015-11-24T10:27:09.377-0300  imported 25359 documents

mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-24T10:27:26.966-0300  connected to: 127.0.0.1
2015-11-24T10:27:26.967-0300  dropping: be-mean.pokemons
2015-11-24T10:27:27.035-0300  imported 610 documents
```

## Fazer um distinct por `cuisine` na collection restaurantes
```
thiago(mongod-3.0.7) be-mean-restaurantes> db.restaurantes.distinct('cuisine')
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
  "Pizza",
  "Continental",
  "Italian",
  "Steak",
  "German",
  "French",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Hotdogs",
  "Not Listed/Not Applicable",
  "Greek",
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

## Fazer um distinct por `types` na collection pokemons
```
thiago(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)
```
thiago(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Rattata"
}
{
  "name": "Charmeleon"
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
Fetched 5 record(s) in 2ms


thiago(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 1ms


thiago(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 2ms
```

## Apresentar quantidade de pokemons de cada `type` (group ou aggregate)
```
db.pokemons.group({
... initial: {total: 0},
... reduce: function (curr, result) {
... curr.types.forEach(function (type) {
... if (result[type]) {
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... });
... }
... })
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

## Realizar 3 counts na pokemons.

1. count -- todos
```
thiago(mongod-3.0.7) be-mean> db.pokemons.count({})
610
```

2. count -- só tipo fogo
```
thiago(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
47
```

3. count -- só de quantos tem a defesa maior que 70
```
thiago(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70} })
250
```