# MongoDB - Aula 02 - Exercício
autor: Fábio Calheiros (conta: fabiocalheiros)

## Crie uma database chamada be-mean-pokemons (passo 1)

	```
	fabio-Inspiron-7520(mongod-3.0.7) test> use be-mean-pokemons
	switched to db be-mean-pokemons
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> 

	```

## Listagem das databases (passo 2)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> show dbs
	be-mean → 0.078GB
	local   → 0.078GB
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> 

	```

## Listagem das coleções (passo 3)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> show collections
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> 

	```

## Cadastro dos pokemons (passo 4)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var pokemon = [{'name':'Electrike','description':'Electrike stores electricity in its long body hair','type': 'Eletric', 'attack': 30, height: 0.6 },{'name':'Blastoise','description':'Blastoise has water spouts that protrude from its shell','type': 'Water', 'attack': 40, height: 1.6 },{'name':'Charizard','description':'Charizard flies around the sky in search of powerful opponents.','type': 'Fire', 'attack': 40, height: 1.7 },{'name':'Jigglypuff','description':'Jigglypuffs vocal cords canfreely adjust the wavelength of its voice','type': 'Normal', 'attack': 20, height: 0.5 },{'name':'Zubat','description':'Zubat remains quietly unmoving ina dark spot during the bright daylight hours','type': 'Poison', 'attack': 20, height: 0.8 }]
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
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

## Lista dos pokemons (passo 5)

	```
	{
	  "_id": ObjectId("5648df98b054309b54e25e0f"),
	  "name": "Electrike",
	  "description": "Electrike stores electricity in its long body hair",
	  "type": "Eletric",
	  "attack": 30,
	  "height": 0.6
	}
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
	  "description": "Charizard flies around the sky in search of powerful opponents.",
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
	Fetched 5 record(s) in 3ms

	```

## Pikachu (passo 6)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Charizard'}
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> poke
	{
	  "_id": ObjectId("5648df98b054309b54e25e11"),
	  "name": "Charizard",
	  "description": "Charizard flies around the sky in search of powerful opponents.",
	  "type": "Fire",
	  "attack": 40,
	  "height": 1.7
	}

	```

## Atualização do Pikachu (passo 7)

	```
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> poke.description = "Pokemon ninja doidao"
	Pokemon ninja doidao
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 39ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
	{
	  "_id": ObjectId("5648df98b054309b54e25e11"),
	  "name": "Charizard",
	  "description": "Pokemon ninja doidao",
	  "type": "Fire",
	  "attack": 40,
	  "height": 1.7
	}
	
	```