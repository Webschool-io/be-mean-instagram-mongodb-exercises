# MongoDB - Aula 03 - Exercício
autor: JOAO PAULO S DE ARAUJO

## 1. Liste todos Pokemons com a altura menor que 1.5
	
	```
	var query = {height: {$lt 1.5}}
	var campos = {name: 1,height: 1}
	db.pokemons.find(query,campos)
	{ "_id" : ObjectId("5647233fddd3df0aacc81f79"), "name" : "luxray", "height" : 1.4 }
	{ "_id" : ObjectId("5643f5ac8a3351185ddd5461"), "name" : "Pikachu", "height" : 0.4 }
	{ "_id" : ObjectId("5643f6e88a3351185ddd5462"), "name" : "bulbassauro", "height" : 0.5 }
	```
	
## 2. Liste todos Pokemons com a altura maior ou igual que 1.5;
	
	
	```
	var query = {height: {$gte: 1.5}}
	db.pokemons.find(query,campos)
	{ "_id" : ObjectId("5647233fddd3df0aacc81f78"), "name" : "heatran", "height" : 1.7 }
	{ "_id" : ObjectId("5647233fddd3df0aacc81f7a"), "name" : "bouffalant", "height" : 1.6 }
	{ "_id" : ObjectId("5647233fddd3df0aacc81f7b"), "name" : "Mega mewtwo Y", "height" : 1.5 }
	{ "_id" : ObjectId("5647233fddd3df0aacc81f7c"), "name" : "Armaldo", "height" : 1.5 }
	```

## 3. Liste todos os Pokemons com a altura menor ou igual que 1.5 E do tipo grama;
	
	```
	var query = {$and: [{height: {$lte: 1.5}},{$or: [{type: 'Grama'},{type: 'grama'}]}]}
	var campos = {name: 1,height: 1,type: 1}
	db.pokemons.find(query,campos)
	{ "_id" : ObjectId("5643f6e88a3351185ddd5462"), "name" : "bulbassauro", "type" : "Grama", "height" : 0.5 }
	```
	
## 4. Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 500;
	
	```
	var poke = db.pokemons.findOne({name: 'Pikachu'})
	poke.attack = 1500
	db.pokemons.save(poke)
	```
	```
	var query = {$or: [{name: 'Pikachu'},{attack: {$lte: 500}}]}
	var campos = {name: 1,attack: 1}
	db.pokemons.find(query,campos)
	{ "_id" : ObjectId("5647233fddd3df0aacc81f78"), "name" : "heatran", "attack" : 500 }
	{ "_id" : ObjectId("5643f5ac8a3351185ddd5461"), "name" : "Pikachu", "attack" : 1500 }
	{ "_id" : ObjectId("5643f6e88a3351185ddd5462"), "name" : "bulbassauro", "attack" : 49 }
	```
	
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 600 E com height menor ou igual que 1.5;
	
	```
	var query = {$and: [{attack: {$gte: 600}},{height: {$lte: 1.5}}]}
	var campos = {name: 1,attack: 1, height: 1}
	db.pokemons.find(query,campos)
	{ "_id" : ObjectId("5647233fddd3df0aacc81f79"), "name" : "luxray", "attack" : 600, "height" : 1.4 }
	{ "_id" : ObjectId("5647233fddd3df0aacc81f7b"), "name" : "Mega mewtwo Y", "attack" : 800, "height" : 1.5 }
	{ "_id" : ObjectId("5647233fddd3df0aacc81f7c"), "name" : "Armaldo", "attack" : 600, "height" : 1.5 }
	{ "_id" : ObjectId("5643f5ac8a3351185ddd5461"), "name" : "Pikachu", "attack" : 1500, "height" : 0.4 }
	```
	