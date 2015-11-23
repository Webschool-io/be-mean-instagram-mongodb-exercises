# MongoDB - Aula 02 - Exercício
autor: JOAO PAULO S DE ARAUJO

## Criação DB (passo 1)
	```
	use be-mean-pokemons
	switched to db be-mean-pokemons
	```
## Listagem das databases (passo 2)
	```
	show dbs
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	local              0.078GB
	test               0.078GB
	```

## Listagem das coleções (passo 3)
	```
	show collections
	```
## Cadastro dos pokemons (passo 4)
	```
	var pokemons = [{name: 'heatran',description:'bicho doido',type:'Lava Dome',attack: 500,defense: 500, height: 1.7},{name: 'luxray',description:'Olhos dourados',type: 'besta',attack: 600,defense: 300,height: 1.4},{name: 'bouffalant',description:'Bufalo bufante',type: 'Bufalis',attack: 600,defense: 400,height: 1.6},{name: 'Mega mewtwo Y',description: 'Criado em laboratório',type: 'Psychic',attack: 800,defense: 300,height: 1.5},{name: 'Armaldo',description: 'Ataca pa karai',type: 'Rock',attack: 600, defense: 400,height: 1.5}]
	pokemons
	[
			{
					"name" : "heatran",
					"description" : "bicho doido",
					"type" : "Lava Dome",
					"attack" : 500,
					"defense" : 500,
					"height" : 1.7
			},
			{
					"name" : "luxray",
					"description" : "Olhos dourados",
					"type" : "besta",
					"attack" : 600,
					"defense" : 300,
					"height" : 1.4
			},
			{
					"name" : "bouffalant",
					"description" : "Bufalo bufante",
					"type" : "Bufalis",
					"attack" : 600,
					"defense" : 400,
					"height" : 1.6
			},
			{
					"name" : "Mega mewtwo Y",
					"description" : "Criado em laboratório",
					"type" : "Psychic",
					"attack" : 800,
					"defense" : 300,
					"height" : 1.5
			},
			{
					"name" : "Armaldo",
					"description" : "Ataca pa karai",
					"type" : "Rock",
					"attack" : 600,
					"defense" : 400,
					"height" : 1.5
			}
	]
	db.pokemons.insert(pokemons)
	BulkWriteResult({
			"writeErrors" : [ ],
			"writeConcernErrors" : [ ],
			"nInserted" : 5,
			"nUpserted" : 0,
			"nMatched" : 0,
			"nModified" : 0,
			"nRemoved" : 0,
			"upserted" : [ ]
	})
```
## Lista dos pokemons (passo 5)
	```
	db.pokemons.find()
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f78"), 
		"name" : "heatran", 
		"description" : "bicho doido", 
		"type" : "Lava Dome",
		"attack" : 500, 
		"defense" : 500, 
		"height" : 1.7 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f79"), 
		"name" : "luxray", 
		"description" : "Olhos dourados", 
		"type" : "besta",
		"attack" : 600, 
		"defense" : 300, 
		"height" : 1.4 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7a"), 
		"name" : "bouffalant", 
		"description" : "Bufalo bufante", 
		"type" : "Bufalis", 
		"attack" : 600, 
		"defense" : 400, 
		"height" : 1.6 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7b"), 
		"name" : "Mega mewtwo Y", 
		"description" : "Criado em laboratório", 
		"type" : "Psychic", 
		"attack" : 800, 
		"defense" : 300, 
		"height" : 1.5 
	}
	{ 
		"_id" : ObjectId("5647233fddd3df0aacc81f7c"), 
		"name" : "Armaldo", 
		"description" : "Ataca pa karai", 
		"type" : "Rock", 
		"attack" : 600, 
		"defense" : 400, 
		"height" : 1.5 
	}
	```
## Pokemon (passo 6)
	```
	var query = {name: 'Armaldo'}
	var poke = db.pokemons.findOne(query)
	poke
	{
			"_id" : ObjectId("5647233fddd3df0aacc81f7c"),
			"name" : "Armaldo",
			"description" : "Ataca pa karai",
			"type" : "Rock",
			"attack" : 600,
			"defense" : 400,
			"height" : 1.5
	}
	```
## Atualização do Pokemon (passo 6)
	```
	var query = {name: 'Armaldo'}
	var poke = db.pokemons.findOne(query)
	poke.description
	Ataca pa karai
	poke.description = 'Mija Lava'
	Mija Lava
	poke.description
	Mija Lava
	db.pokemons.save(poke)
	WriteResult({ 
		"nMatched" : 1,
		"nUpserted" : 0, 
		"nModified" : 1 
	})
	```