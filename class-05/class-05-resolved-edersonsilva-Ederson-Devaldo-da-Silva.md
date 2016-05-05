# MongoDB - Aula 05 - Exercício
autor: Ederson Devaldo da Silva

## Importar as collections restaurantes e pokemons.

```
 mongoimport --host 127.0.0.1 -d be-mean -c restaurantes --drop --file restaurantes.json
2015-12-06T23:59:29.542-0200  connected to: 127.0.0.1
2015-12-06T23:59:29.543-0200  dropping: be-mean.restaurantes
2015-12-06T23:59:32.552-0200  [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
2015-12-06T23:59:33.431-0200  imported 25359 documents

$ mongoimport --host 127.0.0.1 -d be-mean -c pokemons --drop --file pokemons.json
2015-12-07T00:01:02.762-0200  connected to: 127.0.0.1
2015-12-07T00:01:02.762-0200  dropping: be-mean.pokemons
2015-12-07T00:01:02.814-0200  imported 610 documents
```

## Distinct por cuisine na restaurantes.

```
codevops(mongod-3.0.6) be-mean> db.restaurantes.distinct('cuisine')
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

## Distinct por types na pokemons.

```
codevops(mongod-3.0.6) be-mean> db.pokemons.distinct('types')
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

```
codevops(mongod-3.0.6) be-mean> db.pokemons.find().limit(5).skip(5*0)
codevops(mongod-3.0.6) be-mean> db.pokemons.find().limit(5).skip(5*1)
codevops(mongod-3.0.6) be-mean> db.pokemons.find().limit(5).skip(5*2)
```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
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


## Realizar 3 counts na pokemons.

```
-> .count -- todos
odevops(mongod-3.0.6) be-mean> db.pokemons.count()
610

-> .count -- só tipo fogo
codevops(mongod-3.0.6) be-mean> db.pokemons.count({types: 'fire'})
47

-> .count -- só de quantos tem a defesa maior que 70
codevops(mongod-3.0.6) be-mean> db.pokemons.count({defense: {$gt: 70}})
250


```


