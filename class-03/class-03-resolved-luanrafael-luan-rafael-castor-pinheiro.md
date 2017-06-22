# MongoDB - Aula 03 - Exercício
autor: LUAN RAFAEL CASTOR PINHEIRO


## 1 - Liste todos Pokemons com a altura menor que 0.5;
	
	```
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt : 0.5 }}
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
		{
		  "_id": ObjectId("56474c58295d0c12b162b7a7"),
		  "name": "Pikachu",
		  "description": "Rato elétrico bem fofinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("56474e88ee09ff771271032c"),
		  "name": "Bulbassauro",
		  "description": "Chicote de trepadeira",
		  "type": "grama",
		  "attack": 49,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("56474f8fee09ff771271032f"),
		  "name": "Caterpie",
		  "description": "Larva lutadora",
		  "type": "inseto",
		  "attack": 30,
		  "height": 0.3,
		  "defense": 35
		}
		Fetched 3 record(s) in 1ms

	```

## 2 - Liste todos Pokemons com a altura maior ou igual que 0.5;
	
	```
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte : 0.5 }}
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
		{
		  "_id": ObjectId("56474e9fee09ff771271032d"),
		  "name": "Charmander",
		  "description": "Esse é o cão chupando manga defofinho",
		  "type": "fogo",
		  "attack": 52,
		  "height": 0.6
		}
		{
		  "_id": ObjectId("56474ee0ee09ff771271032e"),
		  "name": "Squirtle",
		  "description": "Ejeta água que passarinho não bebe",
		  "type": "água",
		  "attack": 48,
		  "height": 0.5
		}
		Fetched 2 record(s) in 1ms

	```

## 3 - Liste todos Pokemons com a altura maior ou igual que 0.5 e do tipo grama;
	
	```
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {$and :[{height: {$lte : 0.5 }},{"type":"grama"}]}
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
		{
		  "_id": ObjectId("56474e88ee09ff771271032c"),
		  "name": "Bulbassauro",
		  "description": "Chicote de trepadeira",
		  "type": "grama",
		  "attack": 49,
		  "height": 0.4
		}
		Fetched 1 record(s) in 1ms

	```

## 4 - Liste todos Pokemons com name `Pikachu` ou com attack menor ou igual que 0.5;
	
	```
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {$or: [{name: "Pikachu"},{attack: {$lte: 0.5}}]}
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
		{
		  "_id": ObjectId("56474c58295d0c12b162b7a7"),
		  "name": "Pikachu",
		  "description": "Rato elétrico bem fofinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 0.4
		}
		Fetched 1 record(s) in 1ms

	```

## 5 - Liste todos Pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5;
	
	```
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
		ubuntu-luan(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
		{
		  "_id": ObjectId("56474c58295d0c12b162b7a7"),
		  "name": "Pikachu",
		  "description": "Rato elétrico bem fofinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("56474e88ee09ff771271032c"),
		  "name": "Bulbassauro",
		  "description": "Chicote de trepadeira",
		  "type": "grama",
		  "attack": 49,
		  "height": 0.4
		}
		{
		  "_id": ObjectId("56474ee0ee09ff771271032e"),
		  "name": "Squirtle",
		  "description": "Ejeta água que passarinho não bebe",
		  "type": "água",
		  "attack": 48,
		  "height": 0.5
		}
		Fetched 3 record(s) in 3ms

	```
