# MongoDB - Aula 03 - Exercício
autor: Guilherme Henrique Escarabel Silva

## Liste todos Pokemons com a altura menor que 0.5
	
```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = {height: {$lt: 0.5}};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("57104e402ce32ca4a32b0dde"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "Eletric",
	  "attack": 100,
	  "height": 0.4
	}
	Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5;

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = {height: {$gte: 0.5}}
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("570fb2562ce32ca4a32b0dd7"),
	  "name": "Seadra",
	  "description": "Sniper Russo",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "velocity": 50,
	  "category": "dragon",
	  "height": 25
	}
	{
	  "_id": ObjectId("570fb47c2ce32ca4a32b0dd8"),
	  "name": "Surskit",
	  "description": "Aranha Galática",
	  "type": "bug",
	  "attack": 20,
	  "defense": 20,
	  "velocity": 30,
	  "category": "Pond Skater",
	  "height": 1.7
	}
	{
	  "_id": ObjectId("570fb4912ce32ca4a32b0dd9"),
	  "name": "shuppet",
	  "description": "Rouba lençois para se vestir",
	  "type": "Ghost",
	  "attack": 40,
	  "defense": 20,
	  "velocity": 30,
	  "category": "Puppet",
	  "height": 2.3
	}
	{
	  "_id": ObjectId("570fb5902ce32ca4a32b0dda"),
	  "name": "Entei",
	  "description": "Corpo de Tigre, rosto de Gavião e rabo de nuvem",
	  "type": "Fire",
	  "attack": 60,
	  "defense": 40,
	  "velocity": 50,
	  "category": "Volcano",
	  "height": 198
	}
	{
	  "_id": ObjectId("570fd6c12ce32ca4a32b0ddb"),
	  "name": "Gengar",
	  "description": "Típico demônio",
	  "type": "Ghost",
	  "attack": 30,
	  "defense": 30,
	  "velocity": 60,
	  "category": "Shadow",
	  "height": 40.5
	}
	{
	  "_id": ObjectId("570fd80a2ce32ca4a32b0ddc"),
	  "name": "Eevee",
	  "description": "Não preciso nem me mexer para te dominar",
	  "type": "Normal",
	  "attack": 30,
	  "defense": 20,
	  "velocity": 30,
	  "category": "Evolution",
	  "height": 6.5
	}
	{
	  "_id": ObjectId("570fd8ea2ce32ca4a32b0ddd"),
	  "name": "Bunnelby",
	  "description": "Coelho com sprite errada, os pés são as orelhas",
	  "type": "Normal",
	  "attack": 20,
	  "defense": 20,
	  "velocity": 30,
	  "category": "Digging",
	  "height": 5
	}
	Fetched 7 record(s) in 84ms

```

## Liste todos os Pokemons com a altura menor ou igual que 0.5 e do tipo grama

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = {
		$and: [{
			height: {
				$lte:0.5
			}
		},
		{
			type: 'Grama'
		}]
	};

	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
	{
  		"_id": ObjectId("571058142ce32ca4a32b0ddf"),
  		"name": "Gramatildo",
  		"description": "Comedor de alho poró",
  		"type": "Grama",
  		"attack": 100,
  		"height": 0.4
	}
	Fetched 1 record(s) in 2ms
```
 
 ## Liste todos os Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = { 
		$or: [{ 
			name: 'Pikachu' 
		}, 
		{ 
			attack: {
				$lte: 0.5
			} 
		}] 
	};

	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
	{
  		"_id": ObjectId("57104e402ce32ca4a32b0dde"),
  		"name": "Pikachu",
  		"description": "Rato elétrico bem fofinho",
  		"type": "Eletric",
  		"attack": 100,
  		"height": 0.4
	}
	Fetched 1 record(s) in 98ms
```	

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = {
		$and: [{
			attack: {
				$gte: 48
			}
		}, 
		{
			height: {
				$lte: 0.5
			}
		}]
	};
	
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
	{
	  "_id": ObjectId("57104e402ce32ca4a32b0dde"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "Eletric",
	  "attack": 100,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("571058142ce32ca4a32b0ddf"),
	  "name": "Gramatildo",
	  "description": "Comedor de alho poró",
	  "type": "Grama",
	  "attack": 100,
	  "height": 0.4
	}
	Fetched 2 record(s) in 3ms
```	    
	