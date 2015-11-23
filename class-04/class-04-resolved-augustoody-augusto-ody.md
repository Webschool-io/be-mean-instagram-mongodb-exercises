# MongoDB - Aula 04 / 05 - Exercício
autor: Augusto Ody

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
db.pokemons.find(query)
var mod = {$pushAll: {moves: ['ataque rápido', 'investida']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
db.pokemons.find(query)
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida" ] }
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update({}, mod, options)
db.pokemons.find()
{ "_id" : ObjectId("5643ba51b4bf61eba67a67aa"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide", "type" : "terra", "attack" : 100, "height" : 10, "defense" : 110, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba57b4bf61eba67a67ac"), "name" : "Machamp", "description" : "Machamp has the power to hurl anything aside", "type" : "lutador", "attack" : 130, "height" : 16, "defense" : 80, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba5ab4bf61eba67a67ad"), "name" : "Tauros", "description" : "This Pokémon is not satisfied unless it is rampaging at all times", "type" : "normal", "attack" : 100, "height" : 14, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5643ba4eb4bf61eba67a67a9"), "name" : "Blastoise", "description" : "A brutal POKMON with pressurized water jets on its shell. They are used for high speed tackles", "type" : "água", "attack" : 83, "height" : 16, "defense" : 100, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba55b4bf61eba67a67ab"), "name" : "Ninetales", "description" : "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's minde", "type" : "fogo", "attack" : 76, "height" : 11, "defense" : 75, "moves" : [ "desvio" ] }
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null}, }
var options = {upsert: true}
db.pokemons.update(query, mod, options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564dbc99c6d924a2d59c4ae2")
})
db.pokemons.find(query)
{ "_id" : ObjectId("564dbc99c6d924a2d59c4ae2"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in: [/ataque rápido/i, /investida/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in: [/ataque rápido/i, /investida/i, /desvio/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
> var query = {moves: {$in: [/ataque rápido/i, /investida/i, /desvio/i]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5643ba51b4bf61eba67a67aa"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide", "type" : "terra", "attack" : 100, "height" : 10, "defense" : 110, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba57b4bf61eba67a67ac"), "name" : "Machamp", "description" : "Machamp has the power to hurl anything aside", "type" : "lutador", "attack" : 130, "height" : 16, "defense" : 80, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba5ab4bf61eba67a67ad"), "name" : "Tauros", "description" : "This Pokémon is not satisfied unless it is rampaging at all times", "type" : "normal", "attack" : 100, "height" : 14, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5643ba4eb4bf61eba67a67a9"), "name" : "Blastoise", "description" : "A brutal POKMON with pressurized water jets on its shell. They are used for high speed tackles", "type" : "água", "attack" : 83, "height" : 16, "defense" : 100, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba55b4bf61eba67a67ab"), "name" : "Ninetales", "description" : "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's minde", "type" : "fogo", "attack" : 76, "height" : 11, "defense" : 75, "moves" : [ "desvio" ] }
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {type: {$ne: 'elétrico'}}
db.pokemons.find(query)
{ "_id" : ObjectId("5643ba51b4bf61eba67a67aa"), "name" : "Sandslash", "description" : "Sandslash's body is covered by tough spikes, which are hardened sections of its hide", "type" : "terra", "attack" : 100, "height" : 10, "defense" : 110, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba57b4bf61eba67a67ac"), "name" : "Machamp", "description" : "Machamp has the power to hurl anything aside", "type" : "lutador", "attack" : 130, "height" : 16, "defense" : 80, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba5ab4bf61eba67a67ad"), "name" : "Tauros", "description" : "This Pokémon is not satisfied unless it is rampaging at all times", "type" : "normal", "attack" : 100, "height" : 14, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564632c8d2b185d9685a165a"), "name" : "Texugao", "description" : "Porra loca", "type" : "grama", "attack" : 0.5, "height" : 0.2, "defense" : 95, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564db7310f916b12a36158d2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db73b0f916b12a36158d3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564db77a0f916b12a36158d4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("564dbb3be36a3d07be8b9ed9"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "ataque rápido", "investida", "desvio" ] }
{ "_id" : ObjectId("5643ba4eb4bf61eba67a67a9"), "name" : "Blastoise", "description" : "A brutal POKMON with pressurized water jets on its shell. They are used for high speed tackles", "type" : "água", "attack" : 83, "height" : 16, "defense" : 100, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("5643ba55b4bf61eba67a67ab"), "name" : "Ninetales", "description" : "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's minde", "type" : "fogo", "attack" : 76, "height" : 11, "defense" : 75, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564dbc99c6d924a2d59c4ae2"), "name" : "AindaNaoExisteMon", "description" : null, "type" : null, "attack" : null, "height" : null, "defense" : null }
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = {$and: [{moves: {$in: ['investida']}}, {defense: {lte: 49}}]}
db.pokemons.find(query)
//Sem resultados
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and: [{type: /água/i}, {attack: {lt: 50}}]}
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 })
```
