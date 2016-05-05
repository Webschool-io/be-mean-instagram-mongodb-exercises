# Exercício 05 - Resolvido
autor: Carlos Alberto Araujo Barreto

## Passo 1: importar as collections restaurantes e pokemons
```
root@carlos-VirtualBox:/home/carlos/mean/be-mean-instagram/apostila/module-mongodb/data# mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json 
connected to: 127.0.0.1
Tue Nov 24 15:31:33.942 dropping: be-mean.pokemons
Tue Nov 24 15:31:33.995 check 9 610
Tue Nov 24 15:31:33.999 imported 610 objects
root@carlos-VirtualBox:/home/carlos/mean/be-mean-instagram/apostila/module-mongodb/data# mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
Tue Nov 24 15:34:48.322 dropping: be-mean.restaurantes
Tue Nov 24 15:34:49.569 check 9 25359
Tue Nov 24 15:34:49.610 imported 25359 objects

```

## Passo 2: distinct por 'cuisine' na collection restaurantes
```
carlos-VirtualBox(mongod-2.4.9) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
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

## Passo 3: distinct por 'types' na collection pokemons
```
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.distinct('types')
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

## Passo 4: as 3 primeiras páginas com .limit() e .skip() de pokemons (5 em 5)
```
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 2ms
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
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
Fetched 5 record(s) in 2ms
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 41ms

```

## Passo 5: group ou aggregate contando a quantidade de pokemons de cada tipo
```
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(current, result) {
... current.types.forEach(function(type) {
... if(result[type]){
... result[type]++;
... } else { 
... result[type] = 1;
... }
... result.total++;
... });
... }
... });
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

## Passo 6: realizar 3 counts em pokemons. (1 - Todos, 2 somente do tipo fogo, 3 - de todos que tem a defesa maior que 70)
```
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.count()
610
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.count({'types': 'fire'})
47
carlos-VirtualBox(mongod-2.4.9) be-mean> db.pokemons.count({'defense': {$gt: 70}})
250
```
