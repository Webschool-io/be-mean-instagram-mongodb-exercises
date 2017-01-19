# MongoDB - Aula 05 - Exercício

**Autor**: Nicolas Serrato

1. Importar as collections restaurantes e pokemons.json;
2. Distinct por cuisine na restaurantes;
3. Distinct por types na pokemons;
4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5);
5. Um group ou aggregate contando a quantidade de pokemons de cada tipo;
6. Realizar 3 counts na pokemons.

## Importar as collections restaurantes e pokemons.json

```
mongoimport -d be-mean-pokemons -c restaurantes --drop --file ~/Documentos/restaurantes.json
connected to: 127.0.0.1
Thu Jan 19 14:29:40.754 dropping: be-mean-pokemons.restaurantes
Thu Jan 19 14:29:42.823 check 9 25359
Thu Jan 19 14:29:44.756 imported 25359 objects

mongoimport -d be-mean-pokemons -c pokemons --drop --file ~/Documentos/pokemons.json
connected to: 127.0.0.1
Thu Jan 19 14:38:12.838 dropping: be-mean-pokemons.pokemons
Thu Jan 19 14:38:12.867 check 9 610
Thu Jan 19 14:38:12.869 imported 610 objects0
```

## Distinct por cuisine na restaurantes

```js
db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
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

## Distinct por types na pokemons

```js
db.pokemons.distinct('types')
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

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```js
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 15ms
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 10ms
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 6ms
```

## Um group ou aggregate contando a quantidade de pokemons de cada tipo

```js
db.pokemons.group({
  initial: {count: 0},
  reduce: function(curr, result) {
    curr.types.forEach(function(property) {
      if(result[property])
        result[property]++;
      else
        result[property] = 1;
      result.count++;
    })
  }
})
[
  {
    "count": 915,
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

## Realizar 3 counts na pokemons

```js
db.pokemons.count({types: 'fire'})
47

db.pokemons.count({attack: {$gte: 30}})
585

db.pokemons.count({defense: {$lte: 50}})
175
```
