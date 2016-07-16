# MongoDB - Aula 03 - Exercício
autor: Guilherme Catini

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 1)
	
	guilherme-linux(mongod-2.6.10) be-mean-pokemons> var query = {height:{$lt:0.5}}
	guilherme-linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("578a4404689050fd26372fda"),
	  "name": "Calheirosmon",
	  "description": "Impossivel ganhar, roubo muito avançado",
	  "type": "desconhecido",
	  "attack": 45,
	  "defense": 30,
	  "height": 0.2
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fdc"),
	  "name": "Dilmamon",
	  "description": "Fantoche",
	  "type": "desconhecido",
	  "attack": 55,
	  "defense": 25,
	  "height": 0.3
	}
	Fetched 2 record(s) in 1ms

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 2)

	guilherme-linux(mongod-2.6.10) be-mean-pokemons> var query = {height:{$gte:0.5}}

	guilherme-linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("578a4404689050fd26372fd9"),
	  "name": "Lulamon",
	  "description": "Retardado mental chorão da porra",
	  "type": "desconhecido",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.5
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fdb"),
	  "name": "Willismon",
	  "description": "Transa com a bunda",
	  "type": "desconhecido",
	  "attack": 40,
	  "defense": 35,
	  "height": 0.9
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fdd"),
	  "name": "Collormon",
	  "description": "Sem descrição",
	  "type": "desconhecido",
	  "attack": 60,
	  "defense": 45,
	  "height": 0.6
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fde"),
	  "name": "Nevesmon",
	  "description": "Aspirador de pó",
	  "type": "desconhecido",
	  "attack": 65,
	  "defense": 50,
	  "height": 0.7
	}
	Fetched 4 record(s) in 2ms

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 3)

	guilherme-linux(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
	guilherme-linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("578a4404689050fd26372fd9"),
	  "name": "Lulamon",
	  "description": "Retardado mental chorão da porra",
	  "type": "grama",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.5
	}
	Fetched 1 record(s) in 1ms


## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 4)

	guilherme-linux(mongod-2.6.10) be-mean-pokemons> var query = {$or:[{name:'Pikachu'},{attack:{$lte:50}}]}
	guilherme-linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("578a4404689050fd26372fd9"),
	  "name": "Lulamon",
	  "description": "Retardado mental chorão da porra",
	  "type": "grama",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.5
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fda"),
	  "name": "Calheirosmon",
	  "description": "Impossivel ganhar, roubo muito avançado",
	  "type": "desconhecido",
	  "attack": 45,
	  "defense": 30,
	  "height": 0.2
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fdb"),
	  "name": "Willismon",
	  "description": "Transa com a bunda",
	  "type": "desconhecido",
	  "attack": 40,
	  "defense": 35,
	  "height": 0.9
	}
	Fetched 3 record(s) in 1ms

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

	guilherme-linux(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
	guilherme-linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("578a4404689050fd26372fd9"),
	  "name": "Lulamon",
	  "description": "Retardado mental chorão da porra",
	  "type": "grama",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.5
	}
	{
	  "_id": ObjectId("578a4404689050fd26372fdc"),
	  "name": "Dilmamon",
	  "description": "Fantoche",
	  "type": "desconhecido",
	  "attack": 55,
	  "defense": 25,
	  "height": 0.3
	}
	Fetched 2 record(s) in 1ms

