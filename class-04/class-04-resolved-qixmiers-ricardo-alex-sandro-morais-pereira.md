# MongoDB - Class 04 - Exercício
autor: Ricardo Pereira 

## Adicionar dois ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var mod = { $pushAll: {moves: ['cortina de fumaca', 'esquiva']}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var opts = {multi: true}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query,mod,opts)
	Updated 0 record(s) in 80ms
	WriteResult({
	"nMatched": 0,
	"nUpserted": 0,
	"nModified": 0
	})
	```

## Adicionar 1 movimento em todos os pokemons: 'desvio'.

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var options = {multi: true}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)
	Updated 5 existing record(s) in 379ms
	WriteResult({
  	"nMatched": 6,
  	"nUpserted": 0,
  	"nModified": 6
	})
	```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = { name: /AindaNaoExisteMon/i}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var mod = { $setOnInsert:{name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves:[], description:'Sem maiores informacoes'}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var opts = {upsert: true}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, opts)
	Updated 1 new record(s) in 2ms
	WriteResult({
	"nMatched": 0,
	"nUpserted": 1,
	"nModified": 0,
	"_id": ObjectId("564f6447238837328367efa5")
	})
	````

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {moves : {$in:['investida', /cortina de fumaca/i]}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
	```
	
##Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {moves: {$in:[/desvio/i] }}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	{
	"_id": ObjectId("5648b37a375e82ed99d9134f"),
	"name": "Charizard",
	"description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	"attack": 40,
	"defense": 30,
	"height": 5.07,
	"moves": [
		"desvio",
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91350"),
	"name": "Mewtwo",
	"description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.",
	"attack": 60,
	"defense": 40,
	"height": 6.07,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91352"),
	"name": "Butterfree",
	"description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	"attack": 20,
	"defense": 20,
	"height": 3.07,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91353"),
	"name": "Blastoise",
	"description": " Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	"attack": 40,
	"defense": 45,
	"height": 5.03,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91351"),
	"name": "Victini",
	"description": "This Pokémon brings victory. It is said that Trainers with Victini always win, regardless of the type of encounter.",
	"attack": 50,
	"defense": 40,
	"height": 1.04,
	"moves": [
		"desvio"
	]
	}
	Fetched 5 record(s) in 422ms
	
	```
	
##Pesquisar todos os pokemons que não são do tipo elétrico.
	
	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = {type: { $ne: 'eletrico'}}
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	{
	"_id": ObjectId("5648b37a375e82ed99d9134f"),
	"name": "Charizard",
	"description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
	"attack": 40,
	"defense": 30,
	"height": 5.07,
	"moves": [
		"desvio",
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91350"),
	"name": "Mewtwo",
	"description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.",
	"attack": 60,
	"defense": 40,
	"height": 6.07,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91352"),
	"name": "Butterfree",
	"description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
	"attack": 20,
	"defense": 20,
	"height": 3.07,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91353"),
	"name": "Blastoise",
	"description": " Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
	"attack": 40,
	"defense": 45,
	"height": 5.03,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("5648b37a375e82ed99d91351"),
	"name": "Victini",
	"description": "This Pokémon brings victory. It is said that Trainers with Victini always win, regardless of the type of encounter.",
	"attack": 50,
	"defense": 40,
	"height": 1.04,
	"moves": [
		"desvio"
	]
	}
	{
	"_id": ObjectId("564f6447238837328367efa5"),
	"name": "AindaNaoExisteMon",
	"attack": null,
	"height": null,
	"defense": null,
	"moves": [ ],
	"description": "Sem maiores informacoes"
	}
	Fetched 6 record(s) in 4ms
	```
	
##Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]};
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
	```
	
##Remova todos os pokemons do tipo água e com attack menor que 50.
	
	```
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]};
	MBP-de-Ricardo(mongod-3.0.3) be-mean-pokemons> db.pokemons.remove(query);
	Removed 0 record(s) in 3ms
	WriteResult({
	"nRemoved": 0
	})
	```

