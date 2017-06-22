## 1 - Liste todos Pokemons com a altura menor que 0.5
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {height: {$lt: 0.5}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("564524fe6f18e1ae072759f5"),
	  "name": "Rattata",
	  "description": "Roedor pequeno mas cabuloso",
	  "type": "Roedor",
	  "attack": 25,
	  "height": 0.3
	}
	{
	  "_id": ObjectId("564526226f18e1ae072759f7"),
	  "name": "Meowth",
	  "description": "Gato feioso",
	  "type": "Animal",
	  "attack": 20,
	  "height": 0.4,
	  "defense": 20
	}
	{
	  "_id": ObjectId("56509f78d99344afbbfaae77"),
	  "name": "Bubasauro",
	  "description": "Dinossauro muito louco",
	  "type": "grama",
	  "attack": 35,
	  "height": 0.3,
	  "defense": 25
	}
	Fetched 3 record(s) in 2ms
```

## 2 - Liste todos Pokemons com a altura maior ou igual a 0.5
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {height: {$gte: 0.5}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("564525c96f18e1ae072759f6"),
	  "name": "Oddish",
	  "description": "Plantinha engraçada",
	  "type": "Planta",
	  "attack": 30,
	  "height": 0.5,
	  "defense": 10
	}
	{
	  "_id": ObjectId("564526536f18e1ae072759f8"),
	  "name": "Psyduck",
	  "description": "Pato meio louco",
	  "type": "Pato",
	  "attack": 30,
	  "height": 0.8,
	  "defense": 20
	}
	{
	  "_id": ObjectId("564526986f18e1ae072759f9"),
	  "name": "Arcanine",
	  "description": "Cachorro ficou calminho",
	  "type": "Cachorro de fogo",
	  "attack": 60,
	  "height": 1.9,
	  "defense": 40
	}
	Fetched 3 record(s) in 96ms
```

## 3 - Liste todos Pokemons com a altura menor ou igual a 0.5 e do tipo grama
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {$and: [{type: 'grama'}], height: {$lte: 0.5}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("56509f78d99344afbbfaae77"),
	  "name": "Bubasauro",
	  "description": "Dinossauro muito louco",
	  "type": "grama",
	  "attack": 35,
	  "height": 0.3,
	  "defense": 25
	}
	Fetched 1 record(s) in 1ms
```

## 4 - Liste todos os Pokemons com o name 'Pikachu' OU com attack menor ou igual a 0.5
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("56509f78d99344afbbfaae77"),
	  "name": "Bubasauro",
	  "description": "Dinossauro muito louco",
	  "type": "grama",
	  "attack": 0.5,
	  "height": 0.3,
	  "defense": 25
	}
	Fetched 1 record(s) in 2ms
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> 
```

## 5 - Liste todos os Pokemons com o attack MAIOR OU IGUAL A 48 E com height menor ou igual a 0.5
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {$and: [{attack: {$gte: 40}}, {height: {$lte: 0.5}}]}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
```