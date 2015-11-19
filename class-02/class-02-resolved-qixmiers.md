# MongoDB - Class 02 - Exercício
autor: Ricardo Pereira

## Created Data Base

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-instagram> use be-mean-pokemons
	switched to db be-mean-pokemons
	```

## My Data Bases

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> show dbs
	be-mean-instagram → 0.078GB
	be-mean           → 0.078GB
	local             → 0.078GB
	```

## My Collections

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> show collections
	````

## Created my Pokemons (Who are these Pokemons)

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var pokemons = [{name: 'Charizard', description: 'Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.', attack: 40, defense: 30, height: 5.07}, {name: 'Mewtwo', description: 'Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.', attack: 60, defense: 40, height: 6.07},{name:'Victini', description: 'This Pokémon brings victory. It is said that Trainers with Victini always win, regardless of the type of encounter.', attack: 50, defense: 40, height: 1.04 },{name: 'Butterfree', description:'Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.' , attack: 20, defense: 20, height: 3.07 },{name: 'Blastoise', description: ' Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.', attack: 40, defense: 40, height: 5.03}]
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.save(pokemons)
	Inserted 1 record(s) in 2332ms
	BulkWriteResult({
	"writeErrors": [ ],
	"writeConcernErrors": [ ],
	"nInserted": 5,
	"nUpserted": 0,
	"nMatched": 0,
	"nModified": 0,
	"nRemoved": 0,
	"upserted": [ ]
	})
	```
	
#My list of pokemons

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find()
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
	"defense": 40,
	"height": 5.03
	}
	Fetched 5 record(s) in 3ms
	
	```

##Find my pokemon

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {name: 'Blastoise'}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> poke
	{
	"_id": ObjectId("5648b37a375e82ed99d91353"),
	"name": "Blastoise",
	"description": " Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	"attack": 40,
	"defense": 40,
	"height": 5.03
	}
	```
	
##Changed information

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> poke.defense = 45
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	"nMatched": 1,
	"nUpserted": 0,
	"nModified": 1
	})
	```
