# MongoDB - Aula 02 - Exercício
autor: Gustavo Gomes da Fé

## Crie uma database chamada be-mean-pokemons;    
	> use be-mean-pokemons
	switched to db be-mean-pokemons    

## Liste quais databases você possui nesse servidor;    
	be-mean                   → 0.004GB
	be-mean-instagram         → 0.000GB
	be-mean-teste             → 0.000GB
	fidelizzi_api_development → 0.000GB
	local                     → 0.000GB    

## Liste quais coleções você possui nessa database;    
	be-mean-pokemons> show collections

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;    
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'Butterfree','description':'Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.','type':'bug/flying',attack: 45, height: 11, defense: 50}
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 67ms
	WriteResult({
	  "nInserted": 1
	})

	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'Spearow','description':'Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.','type':'voador',attack: 60, height: 3, defense: 30 }
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'Ekans','description':'Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.','type':'venenoso',attack: 60, height: 20, defense: 44 }
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})

	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'Raichu','description':'If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémons nest.','type':'elétrico',attack: 90, height: 8, defense: 55 }
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})

	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'Nidoqueen','description':'Nidoqueens body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.','type':'venenoso',attack: 92, height: 13, defense: 87 }
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 13ms
	WriteResult({
	  "nInserted": 1
	})    

## Liste os pokemons existentes na sua coleção;    
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("5647ed127c289526011c473e"),
	  "name": "Butterfree",
	  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	  "type": "bug/flying",
	  "attack": 45,
	  "height": 11,
	  "defense": 50
	}
	{
	  "_id": ObjectId("5647ee247c289526011c473f"),
	  "name": "Spearow",
	  "description": "Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.",
	  "type": "voador",
	  "attack": 60,
	  "height": 3,
	  "defense": 30
	}
	{
	  "_id": ObjectId("5647ee967c289526011c4740"),
	  "name": "Ekans",
	  "description": "Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.",
	  "type": "venenoso",
	  "attack": 60,
	  "height": 20,
	  "defense": 44
	}
	{
	  "_id": ObjectId("5647ef597c289526011c4741"),
	  "name": "Raichu",
	  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémons nest.",
	  "type": "elétrico",
	  "attack": 90,
	  "height": 8,
	  "defense": 55
	}
	{
	  "_id": ObjectId("5647f00d7c289526011c4742"),
	  "name": "Nidoqueen",
	  "description": "Nidoqueens body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.",
	  "type": "venenoso",
	  "attack": 92,
	  "height": 13,
	  "defense": 87
	}
	Fetched 5 record(s) in 1ms
    

# Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
    
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne({'name':'Buterfree'})	
    

# Modifique sua `description` e salvê-o
    
	Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
    
