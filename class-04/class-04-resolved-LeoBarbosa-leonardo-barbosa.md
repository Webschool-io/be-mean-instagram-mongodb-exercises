# MongoDB - Aula 04 - Exercício
autor: Leonardo Barbosa de Oliveira

## 1- Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

	> var query = {name: {$in : [/pikachu/i,/squirtle/i,/bulbassauro/i
	]} }
	> var mod = {$pushAll: {moves:['investida', 'ataque rápido']}}
	> var options = {multi:true}
	> db.pokemons.update(query, mod, options)
	WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

## 2- Adicionar 1 movimento em todos os pokemons: desvio.
	
	> var query = {}
	> var mod = {$push:{moves:'desvio'}}
	> var options = {multi:true}
	> db.pokemons.update(query,mod,options)

	WriteResult({ "nMatched" : 9, "nUpserted" : 0, "nModified" : 9 })

## 3- Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

	> var query = {name: /AindaNaoExisteMon/i}
	> var mod = {
		$set:{'description': 'Sem maiores informações'},
		$setOnInsert: {
			name: 'AindaNaoExisteMon',
			defese: null,
			height: null
		}
	}
	> var options = {upsert:true}
	>WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564cc234d0d5ed148fbe27a8")
	})

	> db.pokemons.find(query)
	{ 
		"_id" : ObjectId("564cc234d0d5ed148fbe27a8"),
		"description" : "Sem maiores informações",
		"name" : "AindaNaoExisteMon",
		"defese" : null,
		"height" : null
	}


## 4- Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
	
	> var query = { "moves" : { "$all" : [ "investida", "ataque do sono" ] } }
	> db.pokemons.find(query)
	{
		"_id" : ObjectId("5643bac2fc9650b6cfbc0e75"),
		"name" : "Snorlax",
		"description" : "Sleeping",
		"attack" : 6,
		"defense" : 3,
		"height" : 2.1,
		"moves" : [ 
			"desvio",
			"ataque do sono",
			"investida"
		] 
	}

## 5- Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
	
	> var query = {moves: {$all : ['ataque rápido', 'investida']}}
	> db.pokemons.find(query)
	{
		"_id" : ObjectId("564bf4654b444ca84cf7542f"),
		"name" : "Pikachu",
		"description" : "Rato elétrico",
		"attack" : 20,
		"defense" : 15,
		"height" : 0.5,
		"moves" : [
			"investida",
			"ataque rápido",
			"desvio",
		]
	 }
	{
		"_id" : ObjectId("564bf4c94b444ca84cf75430"),
		"name" : "Squirtle",
		"description" : "Bicho dágua",
		"attack" : 25,
		"defense" : 10,
		"height" : 0.9,
		"moves" : [ 
			"investida",
			"ataque rápido",
			"desvio",
		] 
	}
	{
		"_id" : ObjectId("564bf5104b444ca84cf75432"),
		"name" : "Charmander",
		"description" : "Bicho do fogo",
		"attack" : 45,
		"defense" : 26,
		"height" : 1.2,
		"moves" :[
			"investida",
			"ataque rápido",
			"desvio",
		]
	}
	{
		"_id" : ObjectId("564bf4fc4b444ca84cf75431"),
		"name" : "Bulbassauro",
		"description" : "Bicho do mato",
		"attack" : 35,
		"defense" : 20,
		"height" : 0.4,
		"moves": [
			"investida",
			"ataque rápido",
			"investida"
		]
	}


## 6- Pesquisar todos os pokemons que não são do tipo elétrico.
	
	> var query = {type: {$ne : 'elétrico'}}
	> db.pokemons.find(query)
	//todos menos o pikachu

## 7- Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
	
	> var query = {$and: [ { moves: "investida"}, {defense: {$gt: 49}}]}
	> db.pokemons.find(query)
	>

## 8- Remova todos os pokemons do tipo água e com attack menor que 50.

	> var query = {$and : [{type: 'água'},{attack:{$lt: 50} }] }
	> db.pokemons.remove(query)
	WriteResult({ "nRemoved" : 0 })
	>