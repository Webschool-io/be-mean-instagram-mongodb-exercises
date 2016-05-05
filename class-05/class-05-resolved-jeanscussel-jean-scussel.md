#MongoDB - Aula 05 - Exercício

**autor**: Jean Scussel

## Importar as collections restaurantes e pokemons

**restaurantes.json**
```
root@jean-Inspiron-7520:/home/jean# mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file /home/jean/repositorios/be-mean-instagram/apostila/module-mongodb/data/restaurantes.json
2015-11-23T14:34:02.027-0200	connected to: 127.0.0.1
2015-11-23T14:34:02.028-0200	dropping: be-mean.pokemons
2015-11-23T14:34:02.958-0200	imported 25359 document

```
**pokemons.json**
```
root@jean-Inspiron-7520:/home/jean# mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file /home/jean/repositorios/be-mean-instagram/apostila/module-mongodb/data/pokemons.json
2015-11-23T14:35:08.596-0200	connected to: 127.0.0.1
2015-11-23T14:35:08.597-0200	dropping: be-mean.pokemons
2015-11-23T14:35:08.621-0200	imported 610 documents
```
## Fazer um distinct por cuisine na collection restaurantes

```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Hamburgers",
  "American ",
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
  "Bagels/Pretzels",
  "Sandwiches/Salads/Mixed Buffet",
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

## Fazer um distinct por types na collection pokemons

```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "flying",
  "normal",
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

**Primeira página**
```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1}).limit(5)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "name": "Charmander"
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "name": "Charmeleon"
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "name": "Wartortle"
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "name": "Caterpie"
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "name": "Blastoise"
}
Fetched 5 record(s) in 2ms

```
**Segunda página **
```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1}).limit(5).skip(5 * 1)
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "name": "Metapod"
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "name": "Butterfree"
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "name": "Spearow"
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "name": "Kakuna"
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "name": "Farfetchd"
}
Fetched 5 record(s) in 1ms

```
**Terceira página**
```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1}).limit(5).skip(5 * 2)
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "name": "Magnemite"
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "name": "Magneton"
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "name": "Doduo"
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "name": "Seel"
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "name": "Dodrio"
}
Fetched 5 record(s) in 1ms

```
##Apresentar quantidade de pokemons de cada type (group ou aggregate)

```
jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if(result[type]) {
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
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "normal": 78,
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
	jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.count()
	610
```

2. count -- só tipo fogo
```
	jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
	47
```

3. count -- só de quantos tem a defesa maior que 70
```
	jean-Inspiron-7520(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
	250
```
