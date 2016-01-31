# MongoDB - Aula 05 - Exercício
autor: Eduardo Pinheiro Quaresma Castro

## 01. Importar as collections restaurantes e pokemons
```js
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-29T16:55:18.410-0300    connected to: localhost
2016-01-29T16:55:18.411-0300    dropping: be-mean.restaurantes
2016-01-29T16:55:19.837-0300    imported 25359 documents

mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2016-01-31T02:23:48.328-0300    connected to: localhost
2016-01-31T02:23:48.328-0300    dropping: be-mean.pokemons
2016-01-31T02:23:48.348-0300    imported 610 documents
```

## 2. Distinct por cuisine na restaurantes
```js
db.restaurantes.distinct("cuisine").sort()
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

## 3. Distinct por types na pokemons
```js
db.pokemons.distinct("types").sort()
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
Cybertron(mongod-3.0.9) be-mean>  db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 0ms
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
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
  "name": "Metapod"
}
Fetched 5 record(s) in 1ms
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 0ms
```

5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
db.pokemons.group({
    initial: {},
    reduce: function(current, result) {
        current.types.forEach(function(type) {
            if (result[type]) {
                result[type]++;
            } else
                result[type] = 1;
        });
    }
});

[
  {
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

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.count()
610
```

-> .count -- só tipo fogo
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.count({types: 'fire'})
47
```

-> .count -- só de quantos tem a defesa maior que 70
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```