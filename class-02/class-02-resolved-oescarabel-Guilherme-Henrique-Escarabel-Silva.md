# MongoDB - Aula 02 - Exercício
autor: Guilherme Henrique Escarabel Silva

## Crie uma database chamada be-mean-pokemons
	
```
	Guilherme-PC(mongod-3.2.4) be-mean-instagram> use be-mean-pokemons
	switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> show databases
	be-mean           → 0.005GB
	be-mean-instagram → 0.000GB
	contatooh         → 0.000GB
	local             → 0.000GB
	news              → 0.000GB
```

## Insira pelo menos 5 pokemons, utilizando o mesmo padrão de campos utilizados
## name, description, attack, defense e height

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Seadra', 
		description: 'Sniper Russo',
		type: 'water', 
		attack: 30,
		defense: 40, 
		velocity: 50, 
		category: 'Dragon', 
		height: 25.0
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);

	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Surskit', 
		description: 'Aranha Galática', 
		type: 'bug', 
		attack: 20,
		defense: 20, 
		velocity: 30, 
		category: 'Pond Skater', 
		height: 1.7
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);


	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'shuppet', 
		description: 'Rouba lençois para se vestir', 
		type: 'Ghost', 
		attack: 40,
		defense: 20, 
		velocity: 30, 
		category: 'Puppet', 
		height: 2.3
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);


	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Entei', 
		description: 'Corpo de Tigre, rosto de Gavião e rabo de nuvem', 
		type: 'Fire', 
		attack: 60, 
		defense: 40, 
		velocity: 50, 
		category: 'Volcano', 
		height: 198.0
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);


	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Gengar', 
		description: 'Típico demônio', 
		type: 'Ghost', 
		attack: 30,
		defense:30, 
		velocity:60, 
		category: 'Shadow', 
		height:40.5
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);


	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Eevee', 
		description: 'sem oor, que coisa fofa', 
		type: 'Normal', 
		attack: 30,
		defense: 20, 
		velocity: 30, 
		category: 'Evolution', 
		height: 6.5
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);


	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var pokemon = {
		name: 'Bunnelby', 
		description: 'Coelho com sprite errada, os pés são as orelhas', 
		type: 'Normal', 
		attack: 20,
		defense: 20, 
		velocity: 30, 
		category: 'Digging', 
		height: 5.0
	};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.insert(pokemon);
```
 
 ## Liste os pokemons existentes na sua coleção

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.find()
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
	  "description": "sem oor",
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
	Fetched 7 record(s) in 7ms
```	

## Busque um pokemons a sua escolha, pelo nome, e o armazene-o em uma variável chamada 'poke';

```
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var query = {name: 'Eevee'};
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> var poke = db.pokemons.findOne(query);
```	    

## Modifique sua 'description' e salvê-o

```
    Guilherme-PC(mongod-3.2.4) be-mean-pokemons> poke.description = "Não preciso nem me mexer para te dominar";
	Guilherme-PC(mongod-3.2.4) be-mean-pokemons> db.pokemons.save(poke);
	Updated 1 existing record(s) in 188ms
	WriteResult({
  		"nMatched": 1,
  		"nUpserted": 0,
  		"nModified": 1
	})
```	  

	