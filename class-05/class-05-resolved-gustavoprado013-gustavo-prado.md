#MongoDB - Aula 05 - Exercício
autor: Gustavo Prado

## 1 - Importar as collections restaurantes e pokemons

```
gustavo@gustavo-Inspiron-3442:~$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file /home/gustavo/Downloads/restaurantes.json
2015-12-15T15:41:03.708-0200  connected to: 127.0.0.1
2015-12-15T15:41:03.709-0200  dropping: be-mean.restaurantes
2015-12-15T15:41:04.858-0200  imported 25359 documents
gustavo@gustavo-Inspiron-3442:~$ 


gustavo@gustavo-Inspiron-3442:~$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file /home/gustavo/Downloads/pokemons.json
2015-12-15T15:49:22.423-0200  connected to: 127.0.0.1
2015-12-15T15:49:22.424-0200  dropping: be-mean.pokemons
2015-12-15T15:49:22.452-0200  imported 620 documents
```

## 2 - Distinct por "cuisine" na restaurantes

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "Bakery",
  "American ",
  "Irish",
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
  "Steak",
  "Italian",
  "Polish",
  "German",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
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
  "Hotdogs",
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

## 3 - Distinct por "types" na pokemons

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.distinct('types').sort()
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

## 4 - As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Pidgey"
}
{
  "name": "Pidgeotto"
}
{
  "name": "Raticate"
}
{
  "name": "Fearow"
}
{
  "name": "Pikachu"
}
Fetched 5 record(s) in 5ms
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Ekans"
}
{
  "name": "Pidgeot"
}
{
  "name": "Beedrill"
}
{
  "name": "Raichu"
}
{
  "name": "Poliwag"
}
Fetched 5 record(s) in 3ms
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Arbok"
}
{
  "name": "Poliwhirl"
}
{
  "name": "Poliwrath"
}
{
  "name": "Abra"
}
{
  "name": "Kadabra"
}
Fetched 5 record(s) in 1ms
```

## 5 - Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.group({
... ...   initial: { total: 0 },
... ...   reduce: function(current, result) {
... ...     current.types.forEach(function(type) {
... ...       if(result[type]) {
... ...         result[type]++;
... ...       } else {
... ...         result[type] = 1;
... ...       }
... ...       result.total++;
... ...     });
... ...   }
... ... });
[
  {
    "total": 934,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "poison": 54,
    "bug": 58,
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

gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.aggregate([
...   {$unwind: '$types'},
...   {$group: {
...     _id: 'types',
...     count: {$sum: 1}
...   }}
... ]);
{
  "result": [
    {
      "_id": "types",
      "count": 934
    }
  ],
  "ok": 1
}
```

## 6. Realizar 3 counts na pokemons.

### Todos

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.count()
620
```

### Só do tipo `fire`

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
53
```

### Só dos que tem defesa maior que 70

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
263
```