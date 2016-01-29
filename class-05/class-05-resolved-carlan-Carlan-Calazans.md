# MongoDB - Aula 05 - Exercício
autor: Carlan Calazans

## Importar as collections restaurantes e pokemons

```bash
$ mongoimport -d be-mean-pokemons -c restaurant
es --drop --file restaurantes.json
2015-11-22T02:34:09.709+0000    connected to: localhost
2015-11-22T02:34:09.710+0000    dropping: be-mean-pokemons.restaurantes
2015-11-22T02:34:12.709+0000    [######################..] be-mean-pokemons.restaurantes        10.7 MB/11.4 MB (94.6%)
2015-11-22T02:34:12.884+0000    imported 25359 documents
```

```bash
$ mongoimport -d be-mean-pokemons -c pokemons -
-drop --file pokemons.json
2015-11-22T02:34:35.901+0000    connected to: localhost
2015-11-22T02:34:35.903+0000    dropping: be-mean-pokemons.pokemons
2015-11-22T02:34:36.021+0000    imported 610 documents
```

## Fazer um distinct por `cuisine` na collection restaurantes

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.restaurantes.distinct('cuisine')
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

## Fazer um distinct por `types` na collection pokemons

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.distinct('types')
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> // page 1
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {_id:0, name:1}).limit(5).skip(5 * 0)
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 1ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> // page 2
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {_id:0, name:1}).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
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
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> // page 3
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({}, {_id:0, name:1}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 1ms
```

## Apresentar quantidade de pokemons de cada `type` (group ou aggregate)

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.aggregate([
  { $unwind : "$types" },
  {
    $group: {
      total: { $sum: 1 },
      _id: "$types"
    }
  },
  {
    $project: {
      tipo: "$_id", total: 1, _id: 0
    }
  }
])
{
  "result": [
    {
      "total": 28,
      "tipo": "fairy"
    },
    {
      "total": 62,
      "tipo": "psychic"
    },
    {
      "total": 38,
      "tipo": "fighting"
    },
    {
      "total": 38,
      "tipo": "dark"
    },
    {
      "total": 51,
      "tipo": "ground"
    },
    {
      "total": 75,
      "tipo": "grass"
    },
    {
      "total": 40,
      "tipo": "electric"
    },
    {
      "total": 37,
      "tipo": "steel"
    },
    {
      "total": 46,
      "tipo": "rock"
    },
    {
      "total": 77,
      "tipo": "flying"
    },
    {
      "total": 47,
      "tipo": "fire"
    },
    {
      "total": 24,
      "tipo": "ice"
    },
    {
      "total": 61,
      "tipo": "bug"
    },
    {
      "total": 54,
      "tipo": "poison"
    },
    {
      "total": 34,
      "tipo": "ghost"
    },
    {
      "total": 20,
      "tipo": "dragon"
    },
    {
      "total": 105,
      "tipo": "water"
    },
    {
      "total": 78,
      "tipo": "normal"
    }
  ],
  "ok": 1
}
```

## Realizar 3 counts na pokemons.

1) count -- todos

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.count(q)
610
```

2) count -- só tipo fogo

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {types: 'fire'}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.count(q)
47
```

3) count -- só de quantos tem a defesa maior que 70

```bash
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {defense: { $gt: 70 }}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.count(q)
250
```