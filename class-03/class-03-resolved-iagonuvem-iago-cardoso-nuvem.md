# MongoDB - Aula 03 - Exercício
autor: Iago Nuvem

## 1 - Listando todos Pokemons com a altura menor que 0.5;

	> var query = {height : {$lt : 0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564da4e50b47a45b460e4232"), "name" : "Pikachu", "description" : "Rato Elétrico Psicodélico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
	{ "_id" : ObjectId("564db23d77a952f6723bae8f"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

## 2 - Liste todos Pokemons com a altura maior ou igual que 0.5;
 
	> var query = {height : {$gte : 0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564dafafe9a7daec5650c86b"), "name" : "Charmander", "description" : "Esse é o cao chupando manga", "type" : "fogo", "attack" : 52, "height" : 0.6 }
	{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5 }

## 3 - Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

	> var query = {$and : [ {height : {$lt : 0.5}} , {type : 'grama'} ]}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }

## 4 - Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
	
	> var query = {$or : [ {name : 'Pikachu'} , {attack : {$lte : 0.5} } ]}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564da4e50b47a45b460e4232"), "name" : "Pikachu", "description" : "Rato Elétrico Psicodélico", "type" : "electric", "attack" : 100, "height" : 0.4 }

## 5 - Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
	
	> var query = { $and : [{attack : {$gte : 48} } , {height : {$lte : 0.5}}] }
	> db.pokemons.find(query)
	{ "_id" : ObjectId("564da4e50b47a45b460e4232"), "name" : "Pikachu", "description" : "Rato Elétrico Psicodélico", "type" : "electric", "attack" : 100, "height" : 0.4 }
	{ "_id" : ObjectId("564daf81e9a7daec5650c86a"), "name" : "bulbassauro", "description" : "Chicote de Trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
	{ "_id" : ObjectId("564dafbce9a7daec5650c86c"), "name" : "Squirtle", "description" : "Ejeta fluidos vaginais", "type" : "agua", "attack" : 48, "height" : 0.5 }

