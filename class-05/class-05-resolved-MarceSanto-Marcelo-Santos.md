## 1. Importar as collections restaurantes e pokemons
 ```
    C:\Users\marce\Desktop>mongoimport --host 127.0.0.1 --db be-mean-pokemon --collection pokemons --drop --file pokemons.json.txt
    2015-11-25T23:02:12.144-0200    connected to: 127.0.0.1
    2015-11-25T23:02:12.148-0200    dropping: be-mean-pokemon.pokemons
    2015-11-25T23:02:12.569-0200    imported 610 documents

 ```
## 2. Distinct por `cuisine` na restaurantes
 ```
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.restaurantes.distinct("cuisine")
    [
        "American ",
        "Hamburgers",
        "Irish",
        "Bakery",
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
## 3. Distinct por `types` na pokemons
 ```
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.distinct('types')

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
## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 4ms
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 1)
{
    "name": "Metapod"
}
{
    "name": "Butterfree"
}
{
    "name": "Caterpie"
}
{
    "name": "Spearow"
}
{
    "name": "Kakuna"
}
Fetched 5 record(s) in 15ms
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 2)
{
    "name": "Farfetchd"
}
{
    "name": "Magneton"
}
{
    "name": "Magnemite"
}
{
    "name": "Doduo"
}
{
    "name": "Seel"
}
Fetched 5 record(s) in 15ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.group({
...     initial: {
...         total: 0
...     },
...     cond: { defense: { $gt: 40 } },
...     reduce: function (curr, result) {
...         curr.types.forEach(function (type) {
...             if (result[type]) {
...                 result[type]++;
...             } else {
...                 result[type] = 1;
...             }
...             result.total++;
...         });
...     }
... });
[
    {
        "total": 796,
        "fire": 41,
        "water": 92,
        "bug": 54,
        "flying": 67,
        "poison": 45,
        "normal": 59,
        "steel": 37,
        "electric": 31,
        "ice": 21,
        "fighting": 33,
        "grass": 67,
        "ground": 47,
        "fairy": 21,
        "psychic": 55,
        "rock": 45,
        "dark": 30,
        "dragon": 20,
        "ghost": 31
    }
]
```

## 6. Realizar 3 counts na pokemons.
```
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.count()
610
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.count({types: 'fire'})
47
DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemon> db.pokemons.count({defense: { $gt: 70 }})
250
```
