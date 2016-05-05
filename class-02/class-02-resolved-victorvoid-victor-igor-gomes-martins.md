# MongoDB - Aula 02 - Exercício
autor: Victor Igor
## Criando database

	```
	use be-mean-pokemons
	switched to db be-mean-pokemons

	```

## Listagem das databases (passo 2)
	
	```
	show dbs
	local             → 0.078GB
	be-mean-instagram → 0.078GB
	be-mean           → 0.078GB

	```

## Listagem das coleções (passo 3)

	```
	show collections

	```

## Cadastro dos pokemons (passo 4)

	```
	var pokemons = [{'name':'Raichu','description':'if the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.','type':'electric','attack':50,'defence':30,'height':0.8},{'name':'Psyduck','description':'Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers.','type':'Water','attack':30,'defence':20,'height':0.8},{'name':'Arcanine','description':'Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night.','type':'Fire','attack':60,'defence':40,'height':1.9},{'name':'Poliwrath','description':'Poliwraths highly developed, brawny muscles never grow fatigued, however much it exercises.','type':'Water-Flying','attack': 50,'defence':40,'height':1.3},{'name':'Metapod','description':'The shell covering this Pokémons body is as hard as an iron slab.','type':'Bug','attack':10,'defence':30,'height':0.7},{'name':'Arbok','description':'This Pokemon is terrifically strong in order to constrict things with its body.','type':'Poison','attack':40,'defence':30,'height':3.5},{'name':'Golbat','description':'Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night.','type':'Poison-Flying','attack':40,'defence':30,'height':1.6},{'name':'Persian','description':'Persian has six bold whiskers that give it a look of toughness.','type':'Normal','attack':40,'defence':30,'height':1}]
	

	db.pokemons.insert(pokemons)

	Inserted 1 record(s) in 421ms
	BulkWriteResult({
	  "writeErrors": [ ],
	  "writeConcernErrors": [ ],
	  "nInserted": 8,
	  "nUpserted": 0,
	  "nMatched": 0,
	  "nModified": 0,
	  "nRemoved": 0,
	  "upserted": [ ]
	})

	```
## Lista dos pokemons (passo 5)
	
	```	
	db.pokemons.find()

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
  "description": "Persian has six bold whiskers that give it a look of toughness.",
  "type": "Normal",
  "attack": 40,
  "defence": 30,
  "height": 1
}
Fetched 8 record(s) in 5ms

```
## Pikachu (passo 6)
	
	```
	var pokemon = {name: 'Persian'}
 	var poke = db.pokemons.findOne(pokemon)
	
	poke

{
  "_id": ObjectId("564da193ab81d6513c255cb1"),
  "name": "Persian",
  "description": "Persian has six bold whiskers that give it a look of toughness.",
  "type": "Normal",
  "attack": 40,
  "defence": 30,
  "height": 1
}

	```
## Atualização do Pikachu (passo 6)
	
	```
	poke.description = 'Sabe voltar pra sua casa de olhos fechados porque ele é mito'Sabe voltar pra sua casa de olhos fechados porque ele é mito'

	db.pokemons.save(poke)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	```

