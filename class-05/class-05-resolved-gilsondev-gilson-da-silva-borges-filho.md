# MongoDB - Aula 05 - Exercício

Autor: Gilson Filho

## 1. Importar as collections restaurantes e pokemons

```bash
$ mongoimport --host 127.0.0.1:27017 --db=be-mean --collection=restaurantes --drop --file=restaurantes.json
2015-12-06T14:36:48.812-0200    connected to: 127.0.0.1:27017
2015-12-06T14:36:48.812-0200    dropping: mean-mean.restaurantes
2015-12-06T14:36:49.744-0200    imported 25359 documents
```

```bash
$ mongoimport --host 127.0.0.1:27017 --db=be-mean-pokemons --collection=pokemons --drop --file=pokemons.json
2015-12-06T14:40:33.542-0200    connected to: 127.0.0.1:27017
2015-12-06T14:40:33.542-0200    dropping: be-mean-pokemons.pokemons
2015-12-06T14:40:33.560-0200    imported 610 documents
```

## 2. Faça o distinct por `cuisine` na coleção de restaurantes

```bash
be-mean> db.restaurants.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Delicatessen",
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

## 3. Faça o distinct por `types` na coleção de pokemons

```bash
be-mean-pokemons> db.pokemons.distinct('types')
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "electric",
  "steel",
  "poison",
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

## 4. Retorne as primeiras 3 páginas com .limit() e .skip() na coleção de pokemons (5 em 5)

```bash
be-mean-pokemons> db.pokemons.find().limit(5).skip(5 * 0)

{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"

  ]

}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"

  ]

}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"

  ]

}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"

  ]

}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"

  ]

}
Fetched 5 record(s) in 1ms
```

```bash
be-mean-pokemons> db.pokemons.find().limit(5).skip(5 * 1)

{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  
  ]

}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  
  ]

}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  
  ]

}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  
  ]

}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  
  ]

}
Fetched 5 record(s) in 0ms
```

```bash
be-mean-pokemons> db.pokemons.find().limit(5).skip(5 * 2)

{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  
  ]

}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.441502",
  "defense": 45,
  "height": "14",
  "hp": 35,
  "name": "Doduo",
  "speed": 75,
  "types": [
    "normal",
    "flying"
  
  ]

}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  
  ]

}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  
  ]

}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  
  ]

}
```

## 5. Escolha dentre o `group` ou `aggregate` para definir a quantidade de pokemons de cada tipo

```bash
be-mean-pokemons> db.pokemons.group({
	initial: { total: 0 },
	cond: {defense: {$gt: 40}},
	reduce: function(curr, result) {
		curr.types.forEach(function(type) {
			if (result[type]) {
				result[type]++;
			} else {
				result[type] = 1;
			}
			result.total++;
		});
	}
});

[
	{
		"total": 796,
		"fire": 41,
		"water": 92,
		"bug": 54,
		"flying": 67,
		"steel": 37,
		"electric": 31,
		"normal": 59,
		"poison": 45,
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

## 6. Realizar 3 counts na coleção de pokemons

```bash
be-mean-pokemons> db.pokemons.count({types: 'fire'})
47

be-mean-pokemons> db.pokemons.count({attack: {$gt: 20}})
597

be-mean-pokemons> db.pokemons.count({name: /ra/i})
55
```
