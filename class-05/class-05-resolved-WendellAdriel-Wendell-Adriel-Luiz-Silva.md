# MongoDB - Aula 05 - Exercício

Autor: Wendell Adriel Luiz Silva

## Importar as collections restaurantes e pokemons

```
mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
2016-02-04T23:01:08.940-0200    connected to: localhost
2016-02-04T23:01:08.963-0200    dropping: be-mean.restaurantes
2016-02-04T23:01:11.780-0200    imported 25359 documents
```

```
mongoimport -d be-mean -c pokemons --drop --file pokemons.json
2016-02-04T23:01:55.686-0200    connected to: localhost
2016-02-04T23:01:55.689-0200    dropping: be-mean.pokemons
2016-02-04T23:01:55.990-0200    imported 610 documents
```

## Fazer um `distinct` por `cuisine` na collection `restaurantes`

```
be-mean> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Hamburgers",
  "American ",
  "Jewish/Kosher",
  "Bakery",
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

## Fazer um `distinct` por `types` na collection `pokemons`

```
be-mean> db.pokemons.distinct('types')
[
  "normal",
  "water",
  "fire",
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

```
be-mean> var query = {}
be-mean> var fields = { _id : 0, name : 1, attack : 1, defense : 1 }
be-mean> db.pokemons.find(query, fields).limit(5).skip(5 * 0)
{
  "attack": 56,
  "defense": 35,
  "name": "Rattata"
}
{
  "attack": 63,
  "defense": 80,
  "name": "Wartortle"
}
{
  "attack": 64,
  "defense": 58,
  "name": "Charmeleon"
}
{
  "attack": 83,
  "defense": 100,
  "name": "Blastoise"
}
{
  "attack": 20,
  "defense": 55,
  "name": "Metapod"
}
Fetched 5 record(s) in 136ms

be-mean> db.pokemons.find(query, fields).limit(5).skip(5 * 1)
{
  "attack": 30,
  "defense": 35,
  "name": "Caterpie"
}
{
  "attack": 45,
  "defense": 50,
  "name": "Butterfree"
}
{
  "attack": 60,
  "defense": 30,
  "name": "Spearow"
}
{
  "attack": 52,
  "defense": 43,
  "name": "Charmander"
}
{
  "attack": 65,
  "defense": 55,
  "name": "Farfetchd"
}
Fetched 5 record(s) in 37ms

be-mean> db.pokemons.find(query, fields).limit(5).skip(5 * 2)
{
  "attack": 25,
  "defense": 50,
  "name": "Kakuna"
}
{
  "attack": 35,
  "defense": 70,
  "name": "Magnemite"
}
{
  "attack": 60,
  "defense": 95,
  "name": "Magneton"
}
{
  "attack": 85,
  "defense": 45,
  "name": "Doduo"
}
{
  "attack": 45,
  "defense": 55,
  "name": "Seel"
}
Fetched 5 record(s) in 17ms
```

## Apresentar quantidade de pokemons de cada type (group ou aggregate)

```
be-mean> var func = [
  { $unwind : '$types' },
  {
    $group : {
      total : { $sum : 1 },
      _id : '$types'
    }
  },
  {
    $project : {
      type : '$_id',
      total : 1,
      _id : 0
    }
  }
]
be-mean> db.pokemons.aggregate(func)
{
  "waitedMS": NumberLong("0"),
  "result": [
    {
      "total": 24,
      "type": "ice"
    },
    {
      "total": 38,
      "type": "dark"
    },
    {
      "total": 105,
      "type": "water"
    },
    {
      "total": 78,
      "type": "normal"
    },
    {
      "total": 47,
      "type": "fire"
    },
    {
      "total": 61,
      "type": "bug"
    },
    {
      "total": 40,
      "type": "electric"
    },
    {
      "total": 54,
      "type": "poison"
    },
    {
      "total": 77,
      "type": "flying"
    },
    {
      "total": 37,
      "type": "steel"
    },
    {
      "total": 34,
      "type": "ghost"
    },
    {
      "total": 38,
      "type": "fighting"
    },
    {
      "total": 62,
      "type": "psychic"
    },
    {
      "total": 28,
      "type": "fairy"
    },
    {
      "total": 75,
      "type": "grass"
    },
    {
      "total": 51,
      "type": "ground"
    },
    {
      "total": 46,
      "type": "rock"
    },
    {
      "total": 20,
      "type": "dragon"
    }
  ],
  "ok": 1
}
```

## Realizar 3 counts na pokemons

### count -> todos

```
be-mean> db.pokemons.count()
610
```

### count -> apenas types: fire

```
be-mean> var query = { types : 'fire' }
be-mean> db.pokemons.count(query)
47
```

### count -> apenas defense > 70

```
be-mean> var query = { defense: { $gt : 70 } }
be-mean> db.pokemons.count(query)
250
```
