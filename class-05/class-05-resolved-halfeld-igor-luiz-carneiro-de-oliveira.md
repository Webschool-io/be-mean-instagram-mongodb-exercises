# MongoDB - Aula 05 - Exercício
Autor: Igor luíz

## Importando as colleções `Pokemons` e `Restaurantes`

```sh
[Igor@localhost be-mean-instagram-mongodb]$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json 
2016-02-05T20:45:52.126-0200    connected to: 127.0.0.1
2016-02-05T20:45:52.127-0200    dropping: be-mean.pokemons
2016-02-05T20:45:52.143-0200    imported 620 documents

[Igor@localhost be-mean-instagram-mongodb]$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
2016-02-05T20:47:01.220-0200    connected to: 127.0.0.1
2016-02-05T20:47:01.220-0200    dropping: be-mean.restaurantes
2016-02-05T20:47:02.930-0200    imported 25359 documents
```

## Distinct por `cuisine` na collection restaurantes

```sh
localhost(mongod-3.0.8) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "American ",
  "Irish",
  "Hamburgers",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
  "Chinese",
  "Other",
  "Chicken",
  "Caribbean",
  "Turkish",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Steak",
  "Italian",
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
  "Not Listed/Not Applicable",
  "African",
  "Greek",
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

## Distinct na propriedade `type` da collection pokemons

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.distinct('types')
[
  "flying",
  "normal",
  "bug",
  "poison",
  "electric",
  "water",
  "fighting",
  "psychic",
  "grass",
  "fairy",
  "fire",
  "rock",
  "ice",
  "ground",
  "steel",
  "ghost",
  "dark",
  "dragon"
]
```

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
> Coloquei apenas com `name` para melhorar a visualização.

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.find({},{name: true, _id: false}).limit(5).skip(5 * 0)
{
  "name": "Pidgeotto"
}
{
  "name": "Pidgeot"
}
{
  "name": "Beedrill"
}
{
  "name": "Pidgey"
}
{
  "name": "Raticate"
}
Fetched 5 record(s) in 3ms


localhost(mongod-3.0.8) be-mean> db.pokemons.find({},{name: true, _id: false}).limit(5).skip(5 * 1)
{
  "name": "Fearow"
}
{
  "name": "Pikachu"
}
{
  "name": "Ekans"
}
{
  "name": "Raichu"
}
{
  "name": "Arbok"
}
Fetched 5 record(s) in 0ms



localhost(mongod-3.0.8) be-mean> db.pokemons.find({},{name: true, _id: false}).limit(5).skip(5 * 3)
{
  "name": "Machop"
}
{
  "name": "Machoke"
}
{
  "name": "Bellsprout"
}
{
  "name": "Kangaskhan"
}
{
  "name": "Ivysaur"
}
Fetched 5 record(s) in 1ms
```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
localhost(mongod-3.0.8) be-mean> db.pokemons.group({
...   initial: {count: 0},
...   reduce: function(curr, result) {
...     curr.types.forEach(function(property) {
...       if(result[property])
...         result[property]++;
...       else
...         result[property] = 1;
... 
...       result.count++;
...     })
...   }
... })
[
  {
    "count": 934,
    "normal": 79,
    "flying": 81,
    "poison": 54,
    "bug": 58,
    "electric": 47,
    "water": 101,
    "fighting": 42,
    "psychic": 61,
    "grass": 70,
    "fairy": 31,
    "fire": 53,
    "rock": 42,
    "ice": 28,
    "ground": 53,
    "steel": 35,
    "ghost": 34,
    "dark": 35,
    "dragon": 30
  }
]


```


## Realizar 3 `counts` na collection pokemon

#### Count de todos
```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.count()
620
```

#### Count só dos pokemons tipo fogo
```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.count({types: 'fire'})
53
```

#### Count só dos pokemons que tem a defesa maior que 70
```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.count({defense: {$gt: 70}})
263
```
