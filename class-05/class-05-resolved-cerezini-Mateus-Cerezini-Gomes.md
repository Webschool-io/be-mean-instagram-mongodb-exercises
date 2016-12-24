# MongoDB - Aula 05 - Exercício
autor: Mateus Cerezini Gomes

## 1. Importar as collections restaurantes e pokemons
```
mongoimport --db be-mean-instagram --collection pokemons --drop --file be-mean-instagram/Apostila/module-mongodb/src/data/pokemons.json 
2015-12-07T21:04:27.491-0200	connected to: localhost
2015-12-07T21:04:27.492-0200	dropping: be-mean-instagram.pokemons
2015-12-07T21:04:27.725-0200	imported 610 documents

mongoimport --db be-mean-instagram --collection restaurantes --drop --file be-mean-instagram/Apostila/module-mongodb/src/data/restaurantes.json 
2015-12-07T21:04:53.571-0200	connected to: localhost
2015-12-07T21:04:53.572-0200	dropping: be-mean-instagram.restaurantes
2015-12-07T21:04:56.304-0200	imported 25359 documents
```

## 2. Distinct por `cuisine` na restaurantes
```js
be-mean-instagram> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "Bakery",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Chinese",
  "Other",
  "Chicken",
  "Caribbean",
  "Turkish",
  "Donuts",
  "Bagels/Pretzels",
  "Pizza",
  "Continental",
  "Italian",
  "Sandwiches/Salads/Mixed Buffet",
  "Steak",
  "German",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Pizza/Italian",
  "French",
  "Polish",
  "Spanish",
  "Mexican",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Greek",
  "Hotdogs",
  "African",
  "Not Listed/Not Applicable",
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

## 3. Distinct por `types` na pokemons
```js
be-mean-instagram> db.pokemons.distinct('types')
[
  "fire",
  "bug",
  "water",
  "flying",
  "normal",
  "electric",
  "steel",
  "poison",
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

## 4. As primeiras 3 páginas com .limit() e .sort() de pokemons (5 em 5)
```js
be-mean-instagram> db.pokemons.find().limit(5).skip(5*0)
be-mean-instagram> .pokemons.find().limit(5).skip(5*1)
be-mean-instagram> .pokemons.find().limit(5).skip(5*2)
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
be-mean-instagram> db.pokemons.group({
    initial: {total: 0},
    reduce: function (current, result) {
        current.types.forEach(function (type) {
            if (result[type]) result[type]++;
            else result[type] = 1;
            result.total++;
        });
    }
})
[
  {
    "total": 915,
    "fire": 47,
    "bug": 61,
    "water": 105,
    "flying": 77,
    "normal": 78,
    "steel": 37,
    "electric": 40,
    "poison": 54,
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

## 6. Realizar 3 counts na pokemons (todos, tipo fogo, defesa maior que 70)
```js
be-mean-instagram> db.pokemons.count()
610
be-mean-instagram> db.pokemons.count({types: 'fire'})
47
be-mean-instagram> db.pokemons.count({defense: {$gt: 70}})
250
```
