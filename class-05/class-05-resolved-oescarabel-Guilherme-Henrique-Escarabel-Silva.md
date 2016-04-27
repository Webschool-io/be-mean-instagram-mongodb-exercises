# MongoDB - Aula 05 - Exercício
User: [oescarabel](https://www.github.com/oescarabel)
Autor: Guilherme Henrique Escarabel Silva

# Importar as collections `restaurantes` e `pokemons`
```
oescarabel:databases guilhermeescarabel$ mongoimport --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json
2016-04-26T10:50:10.327-0400  connected to: localhost
2016-04-26T10:50:10.341-0400  dropping: be-mean-instagram.restaurantes
2016-04-26T10:50:13.058-0400  imported 25359 documents

oescarabel:databases guilhermeescarabel$ mongoimport --db be-mean-instagram --collection pokemons --drop --file pokemons.json
2016-04-26T10:50:27.655-0400  connected to: localhost
2016-04-26T10:50:27.656-0400  dropping: be-mean-instagram.pokemons
2016-04-26T10:50:28.225-0400  imported 610 documents
oescarabel:databases guilhermeescarabel$ mongoimport --db be-mean-instagram --collection pokemons --drop --file pokemons.json
```

# Distinct por `cuisine` na restaurantes.
```
oescarabel(mongod-3.2.4) be-mean-instagram> db.restaurantes.distinct('cuisine');
[
  "Irish",
  "Bakery",
  "Hamburgers",
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
  "Czech",
  "Bangladeshi",
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

# Distinct por `types` na pokemons.
```
oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.distinct('types');
[
  "fire",
  "water",
  "normal",
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

# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```
oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.find({}, {_id:0, name: 1}).limit(5).skip(5*0);
{
  "name": "Charmeleon"
}
{
  "name": "Charmander"
}
{
  "name": "Wartortle"
}
{
  "name": "Rattata"
}
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 50ms

oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.find({}, {_id:0, name: 1}).limit(5).skip(5*1);
{
  "name": "Blastoise"
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
Fetched 5 record(s) in 2ms

oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.find({}, {_id:0, name: 1}).limit(5).skip(5*2);
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
Fetched 5 record(s) in 3ms
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.group({
...   initial: {total: 0},
...   reduce: function(current, resultado) {
...     current.types.forEach(function(type){
...       if(resultado[type]){
...         resultado[type]++;
...       }else{
...         resultado[type] = 1;
...       }
...       resultado.total++;
...     });
...   }
... });
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "normal": 78,
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

# Realizar 3 counts na pokemons.
```
oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.count({$and:[{defense: {$lte:50}},{speed: {$gt: 20}}]});
164

oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.count({name: /x/i});
19

oescarabel(mongod-3.2.4) be-mean-instagram> db.pokemons.count({types: /ghost/i});
34

```