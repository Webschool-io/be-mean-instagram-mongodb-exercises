# MongoDB - Aula 03 - Exercício
autor: Marcelo santos

## Liste todos Pokemons com a altura **menor que** 0.5;
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("564a5ab6252cbe53958f362d"),
		  "name": "Geodude",
		  "description": "Possui um soco forte",
		  "type": "rocha",
		  "attack": 80,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("564a5ad1252cbe53958f362e"),
		  "name": "Cubone",
		  "description": "Ataque de Osso",
		  "type": "Terra",
		  "attack": 50,
		  "height": 0.4
		}
		Fetched 2 record(s) in 2ms


## Liste todos Pokemons com a altura **maior ou igual que** 0.5
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("564a5ae4252cbe53958f362f"),
		  "name": "Beedrill",
		  "description": "Abelha extremamente nervosa",
		  "type": "inseto",
		  "attack": 90,
		  "height": 1
		}
		{
		  "_id": ObjectId("564a5aee252cbe53958f3630"),
		  "name": "Pidgeotto",
		  "description": "Rajada de Vento",
		  "type": "Passaro",
		  "attack": 60,
		  "height": 1.1
		}
		{
		  "_id": ObjectId("564a5afb252cbe53958f3631"),
		  "name": "Raichu",
		  "description": "Evolução do pikachu",
		  "type": "eletrico",
		  "attack": 90,
		  "height": 0.8
		}
		{
		  "_id": ObjectId("564a5b08252cbe53958f3632"),
		  "name": "Jigglypuff",
		  "description": "Toca um cançao de dormi",
		  "type": "fada",
		  "attack": 45,
		  "height": 0.5
		}
		{
		  "_id": ObjectId("564a5b13252cbe53958f3633"),
		  "name": "Psyduck",
		  "description": "Mais atrapalhado que o mister bean",
		  "type": "agua",
		  "attack": 52,
		  "height": 0.8
		}
		{
		  "_id": ObjectId("564a5b23252cbe53958f3634"),
		  "name": "Alakazam",
		  "description": "Tem medo de fantasmas",
		  "type": "pisiquico",
		  "attack": 50,
		  "height": 1.5
		}
		Fetched 6 record(s) in 3ms


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
		Fetched 0 record(s) in 0ms


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
		Fetched 0 record(s) in 0ms


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
		m4rc3l0(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("564a5ab6252cbe53958f362d"),
		  "name": "Geodude",
		  "description": "Possui um soco forte",
		  "type": "rocha",
		  "attack": 80,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("564a5ad1252cbe53958f362e"),
		  "name": "Cubone",
		  "description": "Ataque de Osso",
		  "type": "Terra",
		  "attack": 50,
		  "height": 0.4
		}
		Fetched 2 record(s) in 2ms
