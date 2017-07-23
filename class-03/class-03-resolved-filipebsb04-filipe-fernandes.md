# MongoDB - Aula 03 - Exercício
autor: Filipe Fernandes


## Liste todos Pokemons com a altura **menor que** 0.5;
	> var query = {height: {$lt: 0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454a"), "name" : "Geodude", "description" : "O COISA quando era apenas uma bebê", "type" : "rock", "attack" : 80, "height" : 0.4 }

	
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
	> var query = {height: {$gte: 0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454b"), "name" : "Graveler", "description" : "O COISA adolescente", "type" : "rock", "attack" : 95, "height" : 1 }
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454c"), "name" : "Golem", "description" : "O COISA aposentado e bem gordinho", "type" : "rock", "attack" : 120, "height" : 1.4 }
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454d"), "name" : "Charmander", "description" : "Dragãozinho com fogo no rabo", "type" : "fire", "attack" : 52, "height" : 0.6 } { "_id" : ObjectId("564a40cf7b37d5be9c4a454e"), "name" : "Charmeleon", "description" : "Dradão chifrudo com fogo no rabo", "type" : "fire", "attack" : 64, "height" : 1.1 }
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454f"), "name" : "Butterfree", "description" : "Borboleta Fofinha", "type" : "flying", "attack" : 45, "height" : 1.1 }
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a4550"), "name" : "Beedrill", "description" : "", "type" : "poison", "attack" : 90, "height" : 1 }


	## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
	> var query = {$and: [{height: {$lte:0.5}},{'type':'grass'}]}
	> db.pokemons.find(query)
	>


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
	> var query = {$or: [{'name': 'Pikachu'},{'attack': {$lte: 0.5}}]}
	> db.pokemons.find(query)                                        
	>                                                                


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
	> var query = {$and: [ {'attack': {$gte: 48}}, {'height': {$lte: 0.5}} ]}	
	>db.pokemons.find(query)
	{ "_id" : ObjectId("564a40cf7b37d5be9c4a454a"), "name" : "Geodude", "description" : "O COISA quando era apenas uma bebê", "type" : "rock", "attack" : 80, "height" : 0.4} 
	>