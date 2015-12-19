# MongoDB - Aula 05 - Exercício
autor: *Iago Nuvem*

## 1. Importar as collections restaurantes e pokemons.

```js
> mongoimport.exe -d be-mean -c pokemons --drop --file pokemons.json
2015-11-24T20:14:20.391-0200    connected to: localhost
2015-11-24T20:14:20.406-0200    dropping: be-mean.pokemons
2015-11-24T20:14:21.729-0200    imported 610 documents


> mongoimport.exe -d be-mean -c restaurantes --drop --file restaurantes.json
2015-11-24T20:24:04.318-0200    connected to: localhost
2015-11-24T20:24:04.318-0200    dropping: be-mean.restaurantes
2015-11-24T20:24:07.316-0200    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2015-11-24T20:24:07.401-0200    imported 25359 documents
```

## 2. Distinct por *cuisine* na restaurantes.

```js

> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Turkish",
  "Chicken",
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

## 3. Distinct por *types* na pokemons.

```js
> db.pokemons.distinct('types')
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```js
// Primeira Página
> db.pokemons.find().limit(5).skip(5 * 0) 

// Segunda Página
> db.pokemons.find().limit(5).skip(5 * 1)

// Terceira Página 
> db.pokemons.find().limit(5).skip(5 * 2) 
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
> db.pokemons.group({
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

```js
// Count em todos os Pokemons
> db.pokemons.count({})
610 

// Count nos Pokemons do tipo 'fire'
> db.pokemons.count({types: 'fire'})
47

// Count nos Pokemons com defesa Maior que 70
> db.pokemons.count({defense: {$gt: 70}})
250
```