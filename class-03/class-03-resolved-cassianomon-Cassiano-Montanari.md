# MongoDB - Aula 03 - Exercício
autor: Cassiano Montanari

## Liste todos os Pokemons com a altura menor que 0.5;

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> query
	{
	  "height": {
		"$lt": 0.5
	  }
	}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	```

## Liste todos os Pokemons com a altura maior ou igual que 0.5;

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbc"),
	  "name": "Cyndaquil",
	  "description": "Raposa humildona que tem fogo nas costas",
	  "type": "fire",
	  "attack": 30,
	  "height": 1.08,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbd"),
	  "name": "Magnemite",
	  "description": "Imã maneiro",
	  "type": "Magnet",
	  "attack": 20,
	  "height": 1,
	  "defense": 30
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbe"),
	  "name": "Chicorita",
	  "description": "Planta zueira",
	  "type": "plant",
	  "attack": 15,
	  "height": 1.4,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbf"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fc0"),
	  "name": "Tortoise",
	  "description": "Tartaruga ninja da agua evoluída",
	  "type": "water",
	  "attack": 35,
	  "height": 1.4,
	  "defense": 40
	}
	Fetched 5 record(s) in 9ms
	```

## Liste todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (plant no meu caso);

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "plant"}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    },
	    {
	      "type": "plant"
	    }
	  ]
	}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	```

## Liste todos os Pokemons com name "Pikachu" OU com attack menor ou igual que 0.5;

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	```

## Liste todos os Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5;

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
	```