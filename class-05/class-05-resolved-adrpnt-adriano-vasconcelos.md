# MongoDB - Aula 05 - Exercício
autor: Adriano Vasconcelos

## Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean-restaurantes --collection restaurantes --drop --file data/restaurantes.json
2015-11-23T13:36:56.820+0000    connected to: 127.0.0.1
2015-11-23T13:36:56.822+0000    dropping: be-mean-restaurantes.restaurantes
2015-11-23T13:36:59.247+0000    imported 25359 documents

mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection pokemons --drop --file data/pokemons.json
2015-11-23T13:37:48.637+0000    connected to: 127.0.0.1
2015-11-23T13:37:48.639+0000    dropping: be-mean-pokemons.pokemons
2015-11-23T13:37:48.675+0000    imported 610 documents
```

## Fazer um distinct por `cuisine` na collection restaurantes
```
db.restaurantes.distinct('cuisine')
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

## Fazer um distinct por `types` na collection pokemons
```
db.pokemons.distinct('types')
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

## Apresentar as primeiras 3 páginas da collection pokemons (5 em 5)
```
db.pokemons.find({}, {_id: 0, name: 1}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 1ms

db.pokemons.find({}, {_id: 0, name: 1}).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
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
Fetched 5 record(s) in 1ms

db.pokemons.find({}, {_id: 0, name: 1}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 2ms
```

## Apresentar quantidade de pokemons de cada `type` (group ou aggregate)
```
db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type){
... if(result[type]){
... result[type]++;
... }else{
... result[type] = 1;
... }
... result.total++;
... });
... }
... })
[
  {
    "total": 915,
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

## Realizar 3 counts na pokemons.

1. count -- todos
```
db.pokemons.count()
610
```

2. count -- só tipo fogo
```
db.pokemons.count({ types: 'fire' })
47
```

3. count -- só de quantos tem a defesa maior que 70
```
db.pokemons.count({ defense: { $gt: 70 } })
250
```