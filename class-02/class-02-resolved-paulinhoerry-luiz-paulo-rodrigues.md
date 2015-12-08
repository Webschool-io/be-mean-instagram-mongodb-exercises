# MongoDB - Aula 02 - Exercício
autor: Luiz Paulo Rodrigues

## Crie uma database chamada be-mean-pokemons
	λ mongo be-mean-pokemons
	2015-12-07T01:02:35.253-0200 I CONTROL  Hotfix KB2731284 or later update is installed, no need to zero-out data files
	MongoDB shell version: 3.0.7
	connecting to: be-mean-pokemons

## Liste quais databases você possui nesse servidor

	> show dbs
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	be-mean-pokemons   0.078GB
	local              0.078GB

## Liste quais coleções você possui nesse database

	> show collections
	pokemons
	system.indexes

## Insira pelo ao menos 5 pokemons a sua escolha

	> var charizard = {"name":"charizard","description":"flies around the sky in search of powerful opponents", "type":"fire", "attack":84, "defense":78 , "height":17}
	WriteResult({ "nInserted" : 1 })

	> var nidoking = {"name":"nidoking","description":"Drilthick tail packs enormously destructive power", "type":"poison", "attack":102, "defense":77, "height":14}
	> db.pokemons.save(addPoke)
	WriteResult({ "nInserted" : 1 })

	> var ninetales = {"name":"ninetales","description":"Casts a sinister light from its bright red eyes to gain total control over its foe's mind", "type":"fire", "attack":76, "defense":75, "height":11}
	> db.pokemons.save(addPoke)
	WriteResult({ "nInserted" : 1 })

	> var arcanine = {"name":"arcanine","description":"fast, stronger and fire", "type":"fire", "attack":110, "defense":80, "height":19}
	> db.pokemons.save(addPoke)
	WriteResult({ "nInserted" : 1 })

	> var gyarados = {"name":"gyarados","description":"its brain cells undergo a structural transformation", "type":"water", "attack":125, "defense":79, "height":65}
	> db.pokemons.save(addPoke)
	WriteResult({ "nInserted" : 1 })

	> var articuno = {"name":"articuno","description":"Is a legendary bird Pokémon that can control ice.", "type":"ice", "attack":85, "defense":100, "height":17}
	> db.pokemons.save(addPoke)
	WriteResult({ "nInserted" : 1 })


## Liste os pokemons existentes na sua coleção

	> db.pokemons.find() {
	    "_id": ObjectId("5664fd4ef1c1c94fcaca1f8a"),
	    "name": "charizard",
	    "description": "flies around the sky in search of powerful opponents",
	    "type": "fire",
	    "attack": 84,
	    "defense": 78,
	    "height": 17
	} {
	    "_id": ObjectId("5664fd80f1c1c94fcaca1f8b"),
	    "name": "nidoking",
	    "description": "Drilthick tail packs enormously destructive power",
	    "type": "poison",
	    "attack": 102,
	    "defense": 77,
	    "height": 14
	} {
	    "_id": ObjectId("5664fd96f1c1c94fcaca1f8c"),
	    "name": "ninetales",
	    "description": "Casts a sinister light from its bright red eyes to gain total control over its foe's mind",
	    "type": "fire",
	    "attack": 76,
	    "defense": 75,
	    "height": 11
	} {
	    "_id": ObjectId("5664fda3f1c1c94fcaca1f8d"),
	    "name": "arcanine",
	    "description": "fast, stronger and fire",
	    "type": "fire",
	    "attack": 110,
	    "defense": 80,
	    "height": 19
	} {
	    "_id": ObjectId("5664fdb4f1c1c94fcaca1f8e"),
	    "name": "gyarados",
	    "description": "its brain cells undergo a structural transformation",
	    "type": "water",
	    "attack": 125,
	    "defense": 79,
	    "height": 65
	} {
	    "_id": ObjectId("5664fdc8f1c1c94fcaca1f8f"),
	    "name": "articuno",
	    "description": "Is a legendary bird Pokémon that can control ice.",
	    "type": "ice",
	    "attack": 85,
	    "defense": 100,
	    "height": 17
	}

## Busque um pokemon pelo nome e armazene-o em uma variável chamada "poke"

	> var poke = {name: "charizard"}
	> db.pokemons.find(poke)
	{ "_id" : ObjectId("5664fd4ef1c1c94fcaca1f8a"), "name" : "charizard", "description" : "flies around the sky in search of powerful opponents", "type" : "fire", "attack" : 84, "defense" : 78, "height" : 17 }

## Modifique sua description e salve-o

	> var p = db.pokemons.findOne(poke)
	> p.name
	charizard
	> p.description = "dragao voador"
	dragao voador
	> p
	{
	        "_id" : ObjectId("5664fd4ef1c1c94fcaca1f8a"),
	        "name" : "charizard",
	        "description" : "dragao voador",
	        "type" : "fire",
	        "attack" : 84,
	        "defense" : 78,
	        "height" : 17
	}