# MongoDB - Aula 03 - Exercício
autor: Victor Igor

## Liste todos Pokemons com a altura **menor que** 0.5 (passo 1)

	```
	var query = {height: {$lt: 0.5}}
	db.pokemons.find(query)

	Fetched 0 record(s) in 1ms

	```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5  (passo 2)
	
	```
	var query = {height: {$gte: 0.5}}
	db.pokemons.find(query)

{
  "_id": ObjectId("564da193ab81d6513c255caa"),
  "name": "Raichu",
  "description": "if the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "electric",
  "attack": 50,
  "defence": 30,
  "height": 0.8
}
{
  "_id": ObjectId("564da193ab81d6513c255cab"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers.",
  "type": "Water",
  "attack": 30,
  "defence": 20,
  "height": 0.8
}
{
  "_id": ObjectId("564da193ab81d6513c255cac"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night.",
  "type": "Fire",
  "attack": 60,
  "defence": 40,
  "height": 1.9
}
{
  "_id": ObjectId("564da193ab81d6513c255cad"),
  "name": "Poliwrath",
  "description": "Poliwraths highly developed, brawny muscles never grow fatigued, however much it exercises.",
  "type": "Water-Flying",
  "attack": 50,
  "defence": 40,
  "height": 1.3
}
{
  "_id": ObjectId("564da193ab81d6513c255cae"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.",
  "type": "Bug",
  "attack": 10,
  "defence": 30,
  "height": 0.7
}
{
  "_id": ObjectId("564da193ab81d6513c255caf"),
  "name": "Arbok",
  "description": "This Pokemon is terrifically strong in order to constrict things with its body.",
  "type": "Poison",
  "attack": 40,
  "defence": 30,
  "height": 3.5
}
{
  "_id": ObjectId("564da193ab81d6513c255cb0"),
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night.",
  "type": "Poison-Flying",
  "attack": 40,
  "defence": 30,
  "height": 1.6
}
{
  "_id": ObjectId("564da193ab81d6513c255cb1"),
  "name": "Persian",
  "description": "Sabe voltar pra sua casa de olhos fechados porque ele é mito",
  "type": "Normal",
  "attack": 40,
  "defence": 30,
  "height": 1
}
	Fetched 8 record(s) in 3ms

	```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama (passo 3)

	```
	var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
	db.pokemons.find(query)

	Fetched 0 record(s) in 0ms

	```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5 (passo 4)

	```
	var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
	db.pokemons.find(query)

	Fetched 0 record(s) in 1ms
	
	```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5 (passo 5)

	```
	var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
	db.pokemons.find(query)

	Fetched 0 record(s) in 0ms

	```