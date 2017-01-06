


# MongoDB - Aula 04 - Exercício
autor: EVELLYN LIMA

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

	> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
	> var mod = {$pushAll: {moves: ['ataque rapido', 'corre muito']}}
	> var options = {multi: true}
	{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque de trovão", "ataque rapido", "corre muito", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585c"), "name" : "Charmander", "description" : "Esse é o cçao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585d"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }

## Adicionar 1 movimento em todos os pokemons: 'desvio'

	> var query = {}
	> var mod = {$push: {moves: 'desvio'}}
	> var options = {multi: true}
	{ "_id" : ObjectId("584368e4841326e66ea9ebb4"), "name" : "Charizard", "description" : "Dragão muito doido que cospe fogo", "type" : "fogo", "attack" : 223, "height" : 1.7, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("58436949841326e66ea9ebb5"), "name" : "Rattata", "description" : "Rato nervoso e tem em todo lugar", "type" : "normal", "attack" : 103, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584369a2841326e66ea9ebb6"), "name" : "Meowth", "description" : "Gato doido", "type" : "normal", "attack" : 92, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584369f0841326e66ea9ebb7"), "name" : "Psyduck", "description" : "Pato fofo doido da porra", "type" : "água", "attack" : 122, "height" : 0.8, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("58436a48841326e66ea9ebb8"), "name" : "Nidorina", "description" : "Muito fofo com cara de bravinho *-*", "type" : "mistico", "attack" : 117, "height" : 0.8, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque de trovão", "ataque rapido", "corre muito", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585c"), "name" : "Charmander", "description" : "Esse é o cçao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585d"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585e"), "name" : "Caterpie", "description" : "Larva lindinha", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585f"), "name" : "Magby", "description" : "Um pato que cospe fogo", "type" : "fogo", "attack" : 35, "height" : 0.7, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf895860"), "name" : "Treecko", "description" : "Largarto marento estiloso", "type" : "grama", "attack" : 30, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf895861"), "name" : "Elgyem", "description" : "Largarto marento estiloso", "type" : "psiquica", "attack" : 35, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584dcdfad3a2f38c924f4f9b"), "description" : "pokemon de teste", "name" : "Testemon", "attack" : 8001, "defense" : 8000, "moves" : [ "investida", "desvio" ], "active" : false }
	{ "_id" : ObjectId("584de2b435fddaca3499add4"), "name" : "pokemoninexistente", "active" : false, "moves" : [ "investida", "desvio" ] }

## Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"

	> var query = {name: /AindaNãoExisteMon/i}
	> var mod = {$setOnInsert: {name: 'AindaNãoExisteMon', attack: null, defense: null, height: null, description: 'Sem mais detalhes'}}
	> var options = {upsert: true}
	{ "_id" : ObjectId("584dfb1435fddaca3499ae08"), "name" : "AindaNãoExisteMon", "attack" : null, "defense" : null, "height" : null, "description" : "Sem mais detalhes" }

## Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

	> var query = {moves: {$all: ['investida', 'corre muito']}}
	{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque de trovão", "ataque rapido", "corre muito", "desvio" ] }

	
## Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.

	> var query = {moves: {$in: ['corre muito', 'ataque rapido']}}
	{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque de trovão", "ataque rapido", "corre muito", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585c"), "name" : "Charmander", "description" : "Esse é o cçao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585d"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }

	
## Pesquisar todos que não são do tipo 'elétrico'

	> var query = {type: {$nin: ['elétrico']}}
	{ "_id" : ObjectId("584368e4841326e66ea9ebb4"), "name" : "Charizard", "description" : "Dragão muito doido que cospe fogo", "type" : "fogo", "attack" : 223, "height" : 1.7, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("58436949841326e66ea9ebb5"), "name" : "Rattata", "description" : "Rato nervoso e tem em todo lugar", "type" : "normal", "attack" : 103, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584369a2841326e66ea9ebb6"), "name" : "Meowth", "description" : "Gato doido", "type" : "normal", "attack" : 92, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584369f0841326e66ea9ebb7"), "name" : "Psyduck", "description" : "Pato fofo doido da porra", "type" : "água", "attack" : 122, "height" : 0.8, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("58436a48841326e66ea9ebb8"), "name" : "Nidorina", "description" : "Muito fofo com cara de bravinho *-*", "type" : "mistico", "attack" : 117, "height" : 0.8, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585a"), "name" : "Pikachu", "description" : "Tato elétrico bem fofinho", "type" : "electic", "attack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "choque de trovão", "ataque rapido", "corre muito", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585c"), "name" : "Charmander", "description" : "Esse é o cçao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585d"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio", "ataque rapido", "corre muito" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585e"), "name" : "Caterpie", "description" : "Larva lindinha", "type" : "inseto", "attack" : 30, "height" : 0.3, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf89585f"), "name" : "Magby", "description" : "Um pato que cospe fogo", "type" : "fogo", "attack" : 35, "height" : 0.7, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf895860"), "name" : "Treecko", "description" : "Largarto marento estiloso", "type" : "grama", "attack" : 30, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584c5db792b43802cf895861"), "name" : "Elgyem", "description" : "Largarto marento estiloso", "type" : "psiquica", "attack" : 35, "height" : 0.5, "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584dcdfad3a2f38c924f4f9b"), "description" : "pokemon de teste", "name" : "Testemon", "attack" : 8001, "defense" : 8000, "moves" : [ "investida", "desvio" ], "active" : false }
	{ "_id" : ObjectId("584de2b435fddaca3499add4"), "name" : "pokemoninexistente", "active" : false, "moves" : [ "investida", "desvio" ] }
	{ "_id" : ObjectId("584dfb1435fddaca3499ae08"), "name" : "AindaNãoExisteMon", "attack" : null, "defense" : null, "height" : null, "description" : "Sem mais detalhes" }

	
## Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49

	var query = {$and: [{moves: 'investida'}, {defense: {$lte: 49}}]}
	Fetched 0 record(s) in 1ms

	
## Remova todos os pokemons do tipo água e com attack menor que 50.

	> db.pokemons.remove(query)
	WriteResult({ "nRemoved" : 1 })