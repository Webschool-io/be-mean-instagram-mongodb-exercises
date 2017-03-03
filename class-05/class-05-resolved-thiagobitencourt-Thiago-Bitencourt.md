# MongoDB - Aula 05 - Exercício
autor: Thiago R. M. Bitencourt

# 1. Importar as collections restaurantes e pokemons

### Restaurantes
```
> mongoimport --host 127.0.0.1 --db be-mean-exercicio-05 --collection restaurantes --drop --file restaurantes.json
2016-07-07T23:47:46.453-0300	connected to: 127.0.0.1
2016-07-07T23:47:46.453-0300	dropping: be-mean-exercicio-05.restaurantes
2016-07-07T23:47:48.449-0300	imported 25359 documents
```

### Pokemons
```
> mongoimport --host 127.0.0.1 --db be-mean-exercicio-05 --collection pokemons --drop --file pokemons.json
2016-07-07T23:49:05.855-0300	connected to: 127.0.0.1
2016-07-07T23:49:05.855-0300	dropping: be-mean-exercicio-05.pokemons
2016-07-07T23:49:05.896-0300	imported 610 documents
```

# 2. Distinct por `cuisine` na collection restaurantes

```
> db.restaurantes.distinct('cuisine')
[
	"Hamburgers",
	"American ",
	"Irish",
	"Bakery",
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
	"Pizza",
	"Continental",
	"Italian",
	"Steak",
	"German",
	"Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
	"Polish",
	"French",
	"Pizza/Italian",
	"Mexican",
	"Spanish",
	"Café/Coffee/Tea",
	"Tex-Mex",
	"Soul Food",
	"Pancakes/Waffles",
	"Seafood",
	"Hotdogs",
	"Not Listed/Not Applicable",
	"African",
	"Greek",
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
> db.restaurantes.distinct('cuisine').length
85
```

# 3. Distinct por `types` na collection pokemons

```
> db.pokemons.distinct('types')
[
	"fire",
	"normal",
	"water",
	"bug",
	"flying",
	"poison",
	"electric",
	"steel",
	"ghost",
	"ice",
	"psychic",
	"fighting",
	"grass",
	"ground",
	"fairy",
	"rock",
	"dark",
	"dragon"
]
> db.pokemons.distinct('types').length
18
```

# 4. As primeiras 3 páginas com .limit() e .skip de pokemons (5 em 5)

```
> var lt = 5;
> var sk = 0;
> db.pokemons.find().limit(lt).skip(lt * sk++)
{ "_id" : ObjectId("564b1dad25337263280d047b"), "attack" : 64, "created" : "2013-11-03T15:05:41.273462", "defense" : 58, "height" : "11", "hp" : 58, "name" : "Charmeleon", "speed" : 80, "types" : [ "fire" ] }
{ "_id" : ObjectId("564b1dad25337263280d0479"), "attack" : 56, "created" : "2013-11-03T15:05:41.305777", "defense" : 35, "height" : "3", "hp" : 30, "name" : "Rattata", "speed" : 72, "types" : [ "normal" ] }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "attack" : 83, "created" : "2013-11-03T15:05:41.282985", "defense" : 100, "height" : "16", "hp" : 79, "name" : "Blastoise", "speed" : 78, "types" : [ "water" ] }
{ "_id" : ObjectId("564b1dad25337263280d047e"), "attack" : 30, "created" : "2013-11-03T15:05:41.285736", "defense" : 35, "height" : "3", "hp" : 45, "name" : "Caterpie", "speed" : 45, "types" : [ "bug" ] }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "attack" : 20, "created" : "2013-11-03T15:05:41.288107", "defense" : 55, "height" : "7", "hp" : 50, "name" : "Metapod", "speed" : 30, "types" : [ "bug" ] }
> db.pokemons.find().limit(lt).skip(lt * sk++)
{ "_id" : ObjectId("564b1dad25337263280d0480"), "attack" : 45, "created" : "2013-11-03T15:05:41.290411", "defense" : 50, "height" : "11", "hp" : 60, "name" : "Butterfree", "speed" : 70, "types" : [ "flying", "bug" ] }
{ "_id" : ObjectId("564b1dad25337263280d0481"), "attack" : 60, "created" : "2013-11-03T15:05:41.310402", "defense" : 30, "height" : "3", "hp" : 40, "name" : "Spearow", "speed" : 70, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dad25337263280d0482"), "attack" : 25, "created" : "2013-11-03T15:05:41.294947", "defense" : 50, "height" : "6", "hp" : 45, "name" : "Kakuna", "speed" : 35, "types" : [ "poison", "bug" ] }
{ "_id" : ObjectId("564b1dae25337263280d0484"), "attack" : 35, "created" : "2013-11-03T15:05:41.435237", "defense" : 70, "height" : "3", "hp" : 25, "name" : "Magnemite", "speed" : 45, "types" : [ "steel", "electric" ] }
{ "_id" : ObjectId("564b1dae25337263280d0483"), "attack" : 65, "created" : "2013-11-03T15:05:41.439497", "defense" : 55, "height" : "8", "hp" : 52, "name" : "Farfetchd", "speed" : 60, "types" : [ "normal", "flying" ] }
> db.pokemons.find().limit(lt).skip(lt * sk++)
{ "_id" : ObjectId("564b1dae25337263280d0485"), "attack" : 60, "created" : "2013-11-03T15:05:41.437483", "defense" : 95, "height" : "10", "hp" : 50, "name" : "Magneton", "speed" : 70, "types" : [ "steel", "electric" ] }
{ "_id" : ObjectId("564b1dae25337263280d0486"), "attack" : 85, "created" : "2013-11-03T15:05:41.441502", "defense" : 45, "height" : "14", "hp" : 35, "name" : "Doduo", "speed" : 75, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dae25337263280d0487"), "attack" : 45, "created" : "2013-11-03T15:05:41.445749", "defense" : 55, "height" : "11", "hp" : 65, "name" : "Seel", "speed" : 45, "types" : [ "water" ] }
{ "_id" : ObjectId("564b1dae25337263280d0488"), "attack" : 110, "created" : "2013-11-03T15:05:41.443720", "defense" : 70, "height" : "18", "hp" : 60, "name" : "Dodrio", "speed" : 100, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dae25337263280d048a"), "attack" : 35, "created" : "2013-11-03T15:05:41.457865", "defense" : 30, "height" : "13", "hp" : 30, "name" : "Gastly", "speed" : 80, "types" : [ "poison", "ghost" ] }
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
> db.pokemons.group({
...   initial: {},
...   cond: {defense: {$gt: 40}},
...   reduce: function(cur, result) {
...     cur.types.forEach(function(type) {
...       if(result[type])
...         result[type]++;
...       else
...         result[type] = 1;
...     });
...   }
... });
[
	{
		"fire" : 41,
		"water" : 92,
		"bug" : 54,
		"flying" : 67,
		"poison" : 45,
		"steel" : 37,
		"electric" : 31,
		"normal" : 59,
		"ice" : 21,
		"fighting" : 33,
		"grass" : 67,
		"ground" : 47,
		"fairy" : 21,
		"psychic" : 55,
		"rock" : 45,
		"dark" : 30,
		"dragon" : 20,
		"ghost" : 31
	}
]
```

# 6. Realizer 3 counts na collection pokemons.

### Total de pokemons
```
> db.pokemons.count({})
610
```

### Total de pokemons do tipo fogo

```
> db.pokemons.count({types: 'fire'})
47
```

### Total de pokemons com defesa maior que 70

```
> db.pokemons.count({defense: {$gt: 70}})
250
```
