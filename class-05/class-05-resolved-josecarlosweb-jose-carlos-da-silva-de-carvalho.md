# MongoDB - Aula 05 - Exercício
autor: José Carlos da Silva de Carvalho

# 1. Importar as collections restaurantes e pokemons
```
carlos@carlos-pc:~/Documentos/Curso BeMEAN$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/Documentos/Curso\ BeMEAN/be-mean-instagram/apostila/module-mongodb/data/restaurantes.json 
2015-12-12T22:33:50.136-0300  connected to: 127.0.0.1
2015-12-12T22:33:50.137-0300  dropping: be-mean.restaurantes
2015-12-12T22:33:50.960-0300  imported 25359 documents
carlos@carlos-pc:~/Documentos/Curso BeMEAN$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/Documentos/Curso\ BeMEAN/be-mean-instagram/apostila/module-mongodb/data/pokemons.json 
2015-12-12T22:42:47.276-0300  connected to: 127.0.0.1
2015-12-12T22:42:47.276-0300  dropping: be-mean.pokemons
2015-12-12T22:42:47.291-0300  imported 610 documents
```

# 2. Distinct por `cuisine` na restaurantes
```
carlos-pc(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Bakery",
  "Hamburgers",
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
  "French",
  "Pizza/Italian",
  "German",
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
  "Vegetarian",
  "Ethiopian",
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

# 3. # 2. Distinct por `types` na pokemons
```
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "fire",
  "normal",
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

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Charmander"
}
{
  "name": "Rattata"
}
{
  "name": "Wartortle"
}
{
  "name": "Metapod"
}
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 1ms
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Blastoise"
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
  "name": "Farfetchd"
}
Fetched 5 record(s) in 1ms
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
  "name": "Charmeleon"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 1ms
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(current, result){
... current.types.forEach(function(type){
... result[type] ? result[type]++ : result[type]=1;
... result.total++;
... });
... }
... })
[
  {
    "total": 915,
    "fire": 47,
    "normal": 78,
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

# 6. Realizar 3 counts na pokemons
```
--> .count -- todos
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.count({})
610

--> .count -- Só tipo fogo
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.count({types: "fire"})
47

--> .count -- defesa maior que 70
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
250

```