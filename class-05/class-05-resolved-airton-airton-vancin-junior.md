# MongoDB - Aula 05 - Exercício
autor: Airton Vancin Junior


## Importar as collections restaurantes e pokemons ##

```
junior@linux:~/www/be-mean-instagram/apostila/module-mongodb/data$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
2015-11-24T23:48:46.157-0200 dropping: be-mean.restaurantes
2015-11-24T23:48:46.705-0200 check 9 25359
2015-11-24T23:48:46.720-0200 imported 25359 objects

junior@linux:~/www/be-mean-instagram/apostila/module-mongodb/data$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json connected to: 127.0.0.1
2015-11-24T23:49:01.596-0200 dropping: be-mean.pokemons
2015-11-24T23:49:01.609-0200 check 9 610
2015-11-24T23:49:01.609-0200 imported 610 objects

```


## Distinct por cuisine na restaurantes ##

```
linux(mongod-2.6.10) be-mean> db.restaurantes.distinct('cuisine').sort()
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

## Distinct por types na pokemons ##

```
linux(mongod-2.6.10) be-mean> db.pokemons.distinct('types').sort()
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

## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5) ##

```
linux(mongod-2.6.10) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 0)
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
linux(mongod-2.6.10) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 1)
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
linux(mongod-2.6.10) be-mean> db.pokemons.find({}, { name: 1, _id: 0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 1ms

```


## Group ou Aggregate contando a quantidade de pokemons de cada tipo ##

```
linux(mongod-2.6.10) be-mean> db.pokemons.group({
... initial: { total: 0 },
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if (result[type]) {
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


## Realizar 3 counts na pokemons. ##
*-> .count -- todos -> .count -- só tipo fogo -> .count -- só de quantos tem a defesa maior que 70*

```
linux(mongod-2.6.10) be-mean> db.pokemons.count({})
610

linux(mongod-2.6.10) be-mean> db.pokemons.count({'types': 'fire'})
47

linux(mongod-2.6.10) be-mean> db.pokemons.count({'defense': {$gt: 70}})
250

```

