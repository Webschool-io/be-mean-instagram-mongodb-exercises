##Fernando Senne Junior

##1 import pokemons
``` 
	C:\bin>mongoimport --db be-mean-pokemons --collection pokemons --file c:/pokemons.json
	2017-03-23T10:46:13.625-0300    connected to: localhost
	2017-03-23T10:46:13.946-0300    imported 610 documents
``` 


##2 distinct 
```
> db.pokemons.distinct('types')
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

##3 limit() e skip()
```
> db.pokemons.find({}, {name:1}).limit(5).skip(0)
	{
	  "_id": ObjectId("564b1dad25337263280d0479"),
	  "name": "Rattata"
	}
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
	  "_id": ObjectId("564b1dad25337263280d047d"),
	  "name": "Blastoise"
	}
	Fetched 5 record(s) in 13ms
```


```
> db.pokemons.find({}, {name:1}).limit(5).skip(5 * 1)
	{
	  "_id": ObjectId("564b1dad25337263280d047e"),
	  "name": "Caterpie"
	}
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
	Fetched 5 record(s) in 40ms
```

```
> db.pokemons.find({}, {name:1}).limit(5).skip(5 * 2)
	{
	  "_id": ObjectId("564b1dae25337263280d0483"),
	  "name": "Farfetchd"
	}
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
	Fetched 5 record(s) in 13ms
```


##4 group contando os tipos de pokemons
```
> db.pokemons.group({   initial: {total:0},   reduce: function(curr, result) {     curr.types.forEach(function(type) {
	 if (result[type]) {         result[type]++;       } else {         result[type] = 1;       }       result.total++     });   } });
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

##5 todos os pokemons
```
	> db.pokemons.count()
	610

##tipo fogo
```
	> db.pokemons.count({types:'fire'}) 
	47                                                                                
```

##defesa maior que 70
```
	> db.pokemons.find({defense: {$gt: 70}}).count()
	250
```