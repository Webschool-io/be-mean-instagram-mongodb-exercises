# MongoDB - Class 03 - Exercício
autor: Ricardo Pereira 

## List of all pokemons with height lass then 0.5

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {height: {$lt: 0.5}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
	```

## List of all pokemons with height greater than or equal 0.5

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {height: {$gte: 0.5}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	{
	"_id": ObjectId("5648b37a375e82ed99d9134f"),
	"name": "Charizard",
	"description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	"attack": 40,
	"defense": 30,
	"height": 5.07
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91350"),
	"name": "Mewtwo",
	"description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.",
	"attack": 60,
	"defense": 40,
	"height": 6.07
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91351"),
	"name": "Victini",
	"description": "This Pokémon brings victory. It is said that Trainers with Victini always win, regardless of the type of encounter.",
	"attack": 50,
	"defense": 40,
	"height": 1.04
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91352"),
	"name": "Butterfree",
	"description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	"attack": 20,
	"defense": 20,
	"height": 3.07
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91353"),
	"name": "Blastoise",
	"description": " Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	"attack": 40,
	"defense": 45,
	"height": 5.03
	}
	Fetched 5 record(s) in 8ms
	```

## List of pokemons with height lass or equal than 0.5 AND type equal gress

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {height: {$gte: 0.5},$and:[{type:'grass'}]}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	````

## List of pokemons with name Pikachu OR with attack less or equal then 0.5

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {name: 'Pikachu',$or:[{attack:{$lte: 0.5}}]}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	```
	
##List of pokemons with attack greater or equal than 48 AND with height lass or equal then 0.5

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {attack: {$gte: 48}, $and:[{height: {$lte: 0.5}}]}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	
	```

