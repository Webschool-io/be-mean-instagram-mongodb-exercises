# MongoDB - Aula 03 - Exercício
autor: Fábio Calheiros (conta: fabiocalheiros)

## Listando todos Pokemons com a altura menor que 0.5 (Passo 1)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5648e8d99f352c534ac8813d"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("5648e96b9f352c534ac8813e"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4
	}
	Fetched 2 record(s) in 1ms

	```

## Listando todos Pokemons com a altura maior ou igual que 0.5 (Passo 2)
	
	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5648df98b054309b54e25e10"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "type": "Water",
	  "attack": 40,
	  "height": 1.6
	}
	{
	  "_id": ObjectId("5648df98b054309b54e25e11"),
	  "name": "Charizard",
	  "description": "Pokemon ninja doidao",
	  "type": "Fire",
	  "attack": 40,
	  "height": 1.7
	}
	{
	  "_id": ObjectId("5648df98b054309b54e25e12"),
	  "name": "Jigglypuff",
	  "description": "Jigglypuffs vocal cords canfreely adjust the wavelength of its voice",
	  "type": "Normal",
	  "attack": 20,
	  "height": 0.5
	}
	{
	  "_id": ObjectId("5648df98b054309b54e25e13"),
	  "name": "Zubat",
	  "description": "Zubat remains quietly unmoving ina dark spot during the bright daylight hours",
	  "type": "Poison",
	  "attack": 20,
	  "height": 0.8
	}
	{
	  "_id": ObjectId("5648e7c79f352c534ac8813c"),
	  "name": "Electrike",
	  "description": "Electrike stores electricity in its long body hair",
	  "type": "Eletric",
	  "attack": 30,
	  "height": 0.6
	}
	{
	  "_id": ObjectId("5648e96b9f352c534ac8813f"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6
	}
	{
	  "_id": ObjectId("5648e96b9f352c534ac88140"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5
	}
	Fetched 7 record(s) in 6ms

	```


## Listando todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (Passo 3)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { type: "grama" }, { height: { $lte: 0.5 } } ] }
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5648e96b9f352c534ac8813e"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4
	}
	Fetched 1 record(s) in 1ms

	```

## Listando todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5; (Passo 4)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ { name: "Pikachu" }, { attack: { $lte: 0.5 } } ] }
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5648e8d99f352c534ac8813d"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4
	}
	Fetched 1 record(s) in 4ms

	```

## Listando todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5; (Passo 5)

	```

	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] }
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5648e8d99f352c534ac8813d"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("5648e96b9f352c534ac8813e"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("5648e96b9f352c534ac88140"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5
	}
	Fetched 3 record(s) in 2ms


	```
