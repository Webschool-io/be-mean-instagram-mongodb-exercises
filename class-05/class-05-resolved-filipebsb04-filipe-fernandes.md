# MongoDB - Aula 05 - Exercício
autor: Filipe Fernandes

## 1. Importar os restaurantes e pokemons:

```

**Restaurantes**
	C:\data
	λ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
	2015-12-02T09:06:23.327-0200    connected to: localhost
	2015-12-02T09:06:23.333-0200    dropping: be-mean.restaurantes
	2015-12-02T09:06:24.875-0200    imported 25359 documents

**Pokemons**
	C:\data
	λ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
	2015-12-02T09:05:19.894-0200    connected to: localhost
	2015-12-02T09:05:19.900-0200    dropping: be-mean.pokemons
	2015-12-02T09:05:20.137-0200    imported 610 documents

```

## 2. Fazer um distinct nos restaurantes por cuisine:

```
	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
	[
		"Irish",
		"American ",
		"Jewish/Kosher",
		"Delicatessen",
		"Ice Cream, Gelato, Yogurt, Ices",
		"Chinese",
		"Bakery",
		"Other",
		"Chicken",
		"Hamburgers",
		"Turkish",
		"Caribbean",
		"Donuts",
		"Sandwiches/Salads/Mixed Buffet",
		"Bagels/Pretzels",
		"Continental",
		"Pizza",
		"Italian",
		"Polish",
		"Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
		"German",
		"Steak",
		"French",
		"Pizza/Italian",
		"Mexican",
		"Spanish",
		"Café/Coffee/Tea",
		"Tex-Mex",
		"Pancakes/Waffles",
		"Soul Food",
		"Hotdogs",
		"Greek",
		"Seafood",
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

## 3. Fazer um distinct nos pokemons por tipo:

```

	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.distinct('types')
	[
		"normal",
		"water",
		"fire",
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

## 4. As primeiras 3 paginas com .limit() e .skip() de pokemons (5 em 5):

```

	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {}
	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var mod = {name: 1, _id: 0}
	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query, mod).limit(5).skip(5 * 0)
	{
		"name": "Rattata"
	}
	{
		"name": "Wartortle"
	}
	{
		"name": "Charmander"
	}
	{
		"name": "Blastoise"
	}
	{
		"name": "Metapod"
	}
	Fetched 5 record(s) in 8ms
	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query, mod).limit(5).skip(5 * 1)
	{
		"name": "Caterpie"
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
	Fetched 5 record(s) in 49ms
	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query, mod).limit(5).skip(5 * 2)
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
	{
		"name": "Dodrio"
	}
	Fetched 5 record(s) in 21ms

```

## 5. Group ou aggregate contando a quantidade de pokemons de cada tipo:

```

**Group**

	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.group({
	... initial: {total: 0},
	... reduce: function(curr, result){
	... curr.types.forEach(function(type){
	... if(result[type]){
	... result[type]++;
	... }else{
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
			"water": 105,
			"fire": 47,
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

**Aggregate**

	FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.aggregate([{
	...   $unwind: "$types"}, {
	...   $group: {
	...     _id: "$types",
	...     count: {$sum: 1}
	...   }
	... }])
	{
	    "result": [
	        {
	            "_id": "fairy",
	            "count": 28
	        },
	        {
	            "_id": "psychic",
	            "count": 62
	        },
	        {
	            "_id": "fighting",
	            "count": 38
	        },
	        {
	            "_id": "dark",
	            "count": 38
	        },
	        {
	            "_id": "ground",
	            "count": 51
	        },
	        {
	            "_id": "grass",
	            "count": 75
	        },
	        {
	            "_id": "electric",
	            "count": 40
	        },
	        {
	            "_id": "steel",
	            "count": 37
	        },
	        {
	            "_id": "rock",
	            "count": 46
	        },
	        {
	            "_id": "flying",
	            "count": 77
	        },
	        {
	            "_id": "fire",
	            "count": 47
	        },
	        {
	            "_id": "ice",
	            "count": 24
	        },
	        {
	            "_id": "bug",
	            "count": 61
	        },
	        {
	            "_id": "poison",
	            "count": 54
	        },
	        {
	            "_id": "ghost",
	            "count": 34
	        },
	        {
	            "_id": "dragon",
	            "count": 20
	        },
	        {
	            "_id": "water",
	            "count": 105
	        },
	        {
	            "_id": "normal",
	            "count": 78
	        }
	    ],
	    "ok": 1
	}


```

## 6. Realizar 3 counts na pokemons:

```
FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count()
610

FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {types: /normal/i}
FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count(query)
78

FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {speed: {$lte: 50}}
FilipeFernandes(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count(query)
218

```
