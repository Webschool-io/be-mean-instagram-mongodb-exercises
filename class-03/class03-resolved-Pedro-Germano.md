# MongoDB - Aula 03 - Exercício
	autor: Pedro Germano

## Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)
	pedrogermano(mongod-3.2.10) test> use be-mean-pokemons
	switched to db be-mean-pokemons
	pedrogermano(mongod-3.2.10) be-mean-pokemons>

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)

	pedrogermano be-mean-pokemons> db.pokemons.find({'height':{$lt:'0.5'}})

	{
		"_id": ObjectId("580bf7881211a6a96a3acdda"),
		"name": "Pikachu",
		"description": "Rato elétrico bem fofinho",
		"type": "eletric",
		"attack": "55",
		"height": "0.4"
	}

	Fetched 1 record(s) in 1ms
	pedrogermanomongod-3.2.10) be-mean-pokemons> 

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)

	 	 pedrogermano(mongod-3.2.10) be-mean-pokemons> var query = {'height':{$gte:'0.5'}}
		 pedrogermano(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query)
		{
		"_id": ObjectId("580bf9b01211a6a96a3acddb"),
		"name": "Psyduck",
		"description": "Este pokemon possui um poder misterioso",
		"type": "água",
		"attack": "52",
		"height": "8",
		"defense": "48"
	}
	{
		"_id": ObjectId("580bf9d61211a6a96a3acddc"),
		"name": "Jigglypuff",
		"description": "Pokemon cantor",
		"type": "fada",
		"attack": "45",
		"height": "5",
		"defense": "20"
	}
	{
		"_id": ObjectId("580bfa991211a6a96a3acddd"),
		"name": "Squirtle",
		"description": "Ejeta água que passarinho não bebe",
		"type": "água",
		"attack": "48",
		"height": "0.5"
	}
	{
		"_id": ObjectId("580bfac31211a6a96a3acdde"),
		"name": "Growlithe",
		"description": "Este pokemon usa o seu sentido olfativo avançado para determinar as emoções",
		"type": "fogo",
		"attack": "70",
		"height": "7",
		"defense": "45"
	}
	Fetched 4 record(s) in 2ms
	pedrogermano(mongod-3.2.10) be-mean-pokemons> 


## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)

	 pedrogermano(mongod-3.2.10) be-mean-pokemons> var query = { $and:[{height: {$lte: "0.5"}}, {type: "grama"}]}
	 pedrogermano(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("580bfb7f1211a6a96a3acddf"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": "49",
		"height": "0.4"
	}
	Fetched 1 record(s) in 1ms
	pedrogermano(mongod-3.2.10) be-mean-pokemons> 


## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)
	pedrogermano(mongod-3.2.10) be-mean-pokemons> var query = {$or:[{name:'Pikachu'},{attack:{$lte: "0.5"}}]}
	pedrogermano(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("580bf7881211a6a96a3acdda"),
		"name": "Pikachu",
		"description": "Rato elétrico bem fofinho",
		"type": "eletric",
		"attack": "55",
		"height": "0.4"
	}
	Fetched 1 record(s) in 1ms
	pedrogermano(mongod-3.2.10) be-mean-pokemons> 

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)
    pedrogermano(mongod-3.2.10) be-mean-pokemons> var query = {$and:[{attack:{$gte:"48"}},{height:{$lte:"0.5"}}]}
    pedrogermano(mongod-3.2.10) be-mean-pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("580bf7881211a6a96a3acdda"),
		"name": "Pikachu",
		"description": "Rato elétrico bem fofinho",
		"type": "eletric",
		"attack": "55",
		"height": "0.4"
	}
	{
		"_id": ObjectId("580bfa991211a6a96a3acddd"),
		"name": "Squirtle",
		"description": "Ejeta água que passarinho não bebe",
		"type": "água",
		"attack": "48",
		"height": "0.5"
	}
	{
		"_id": ObjectId("580bfb7f1211a6a96a3acddf"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": "49",
		"height": "0.4"
	}
	Fetched 3 record(s) in 2ms
