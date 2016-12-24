# MongoDB - Aula 05 - Exercício
autor: Samuel Desconsi - Underzzoo

## 1. Importar as collections restaurantes e pokemons

```
code@code-NH4CU03:~/Documentos/Github$ mongoimport -h localhost -d pokemons -file /home/code/Documentos/Github/MongoDb-ebook/src/data/pokemons.json
connected to: localhost
no collection specified!
using filename 'pokemons' as collection.
2016-10-27T20:59:13.186-0200 check 9 610
2016-10-27T20:59:13.236-0200 imported 610 objects

> show dbs
admin             (empty)
be-mean           0.078GB
be-mean-pokemons  0.078GB
livros            0.078GB
local             0.078GB
pokemons          0.078GB
test              0.078GB

> use pokemons
switched to db pokemons

> show collections
pokemons
system.indexes

> db.pokemons.count()
610


```

## 2. Distinct por 'cuisine' na restaurantes

```

> use be-mean
switched to db be-mean
> db.restaurantes.distinct('cuisine')
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
## 3. Distinct por 'Types' na pokemons

```
> db.pokemons.distinct('types').sort()
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

## 4. As 3 primeiras páginas com .limit() e .skip() de pokemons (5 em 5)

```
> db.pokemons.find({}, {name: 1}).limit(5).skip(5 * 0)
{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "name" : "Charmeleon" }
{ "_id" : ObjectId("564b1dad25337263280d047c"), "name" : "Wartortle" }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
> db.pokemons.find({}, {name: 1}).limit(5).skip(5 * 1)
{ "_id" : ObjectId("564b1dad25337263280d047e"), "name" : "Caterpie" }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "name" : "Metapod" }
{ "_id" : ObjectId("564b1dad25337263280d0480"), "name" : "Butterfree" }
{ "_id" : ObjectId("564b1dad25337263280d0481"), "name" : "Spearow" }
{ "_id" : ObjectId("564b1dad25337263280d0482"), "name" : "Kakuna" }
> db.pokemons.find({}, {name: 1}).limit(5).skip(5 * 2)
{ "_id" : ObjectId("564b1dae25337263280d0483"), "name" : "Farfetchd" }
{ "_id" : ObjectId("564b1dae25337263280d0484"), "name" : "Magnemite" }
{ "_id" : ObjectId("564b1dae25337263280d0485"), "name" : "Magneton" }
{ "_id" : ObjectId("564b1dae25337263280d0486"), "name" : "Doduo" }
{ "_id" : ObjectId("564b1dae25337263280d0487"), "name" : "Seel" }
>

```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.aggregate([
  { $unwind: '$types' },
  { $group: {
      _id: 0,
      count: { $sum: 1 }
      }
  }
]);

{ "_id" : "fairy", "count" : 28 }
{ "_id" : "psychic", "count" : 62 }
{ "_id" : "fighting", "count" : 38 }
{ "_id" : "ghost", "count" : 34 }
{ "_id" : "dark", "count" : 38 }
{ "_id" : "ground", "count" : 51 }
{ "_id" : "grass", "count" : 75 }
{ "_id" : "electric", "count" : 40 }
{ "_id" : "steel", "count" : 37 }
{ "_id" : "bug", "count" : 61 }
{ "_id" : "poison", "count" : 54 }
{ "_id" : "fire", "count" : 47 }
{ "_id" : "ice", "count" : 24 }
{ "_id" : "rock", "count" : 46 }
{ "_id" : "flying", "count" : 77 }
{ "_id" : "dragon", "count" : 20 }
{ "_id" : "water", "count" : 105 }
{ "_id" : "normal", "count" : 78 }


```
## 6. Realizar 3 counts na pokemons.

```
> db.pokemons.count({defense: {$gte: 35}})
579
> db.pokemons.count({attack: {$gte: 35}})
567
> db.pokemons.count({speed: {$gte: 20}})
597

```
