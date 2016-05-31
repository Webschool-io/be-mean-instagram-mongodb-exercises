# MongoDB - Aula 02 - Exercício
autor: Cassiano Montanari

## Crie uma database chamada be-mean-pokemon;

	```
	macmini(mongod-3.2.6) be-mean-instagram> use be-mean-pokemon
	switched to db be-mean-pokemon
	```

## Liste quais databases você possui nesse servidor;

	```
	macmini(mongod-3.2.6) be-mean-pokemon> show dbs
	be-mean-instagram → 0.005GB
	local             → 0.000GB
	```

## Liste quais coleções você possui nessa database;

	```
	macmini(mongod-3.2.6) be-mean-pokemon> show collections
	macmini(mongod-3.2.6) be-mean-pokemon>
	```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

	```
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert({"name":"Cyndaquil","description":"Raposa humildona que tem fogo nas costas","type":"fire",attack:30,height:1.08,defense:20})
	Inserted 1 record(s) in 673ms
	WriteResult({
	  "nInserted": 1
	})
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert({"name":"Magnemite","description":"Imã maneiro","type":"Magnet",attack:20,height:1.00,defense:30})
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert({"name":"Chicorita","description":"Planta zueira","type":"plant",attack:15,height:1.40,defense:20})
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert({"name":"Squirtle","description":"Tartaruga ninja da agua","type":"water",attack:25,height:0.8,defense:20})
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert({"name":"Tortoise","description":"Tartaruga ninja da agua evoluída","type":"water",attack:35,height:1.4,defense:40})
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	```

## Liste os pokemons existentes na sua coleção;

	```
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.find()
	{
	  "_id": ObjectId("574dd01f8d48c026d9e4fb0f"),
	  "name": "Cyndaquil",
	  "description": "Raposa humildona que tem fogo nas costas",
	  "type": "fire",
	  "attack": 30,
	  "height": 1.08,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574dd0ce8d48c026d9e4fb10"),
	  "name": "Magnemite",
	  "description": "Imã maneiro",
	  "type": "Magnet",
	  "attack": 20,
	  "height": 1,
	  "defense": 30
	}
	{
	  "_id": ObjectId("574dd0f48d48c026d9e4fb11"),
	  "name": "Chicorita",
	  "description": "Planta zueira",
	  "type": "plant",
	  "attack": 15,
	  "height": 1.4,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574dd1208d48c026d9e4fb12"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20
	}
	{
	  "_id": ObjectId("574dd1388d48c026d9e4fb13"),
	  "name": "Tortoise",
	  "description": "Tartaruga ninja da agua evoluída",
	  "type": "water",
	  "attack": 35,
	  "height": 1.4,
	  "defense": 40
	}
	Fetched 5 record(s) in 4ms
	```

## Busque um pokemon a sua escolha utilizando o "name" e armazene-o em uma variável chamada 'poke';

	```
	macmini(mongod-3.2.6) be-mean-pokemon> var poke = {name: "Squirtle"}
	macmini(mongod-3.2.6) be-mean-pokemon> var p = db.pokemons.findOne(poke)
	macmini(mongod-3.2.6) be-mean-pokemon> p
	{
	  "_id": ObjectId("574dd1208d48c026d9e4fb12"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20
	}
	macmini(mongod-3.2.6) be-mean-pokemon>
	```

## Modifique sua 'description' e salvê-o

	```
	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.update({name:"Squirtle"},{$set:{description:"Tartaruga ninja da agua com description alterada"}})
	Updated 1 existing record(s) in 72ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	macmini(mongod-3.2.6) be-mean-pokemon> var poke = {name: "Squirtle"}
	macmini(mongod-3.2.6) be-mean-pokemon> var p = db.pokemons.findOne(poke)
	macmini(mongod-3.2.6) be-mean-pokemon> p
	{
	  "_id": ObjectId("574dd1208d48c026d9e4fb12"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua com description alterada",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20
	}

	macmini(mongod-3.2.6) be-mean-pokemon> db.pokemons.save(poke)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	```
