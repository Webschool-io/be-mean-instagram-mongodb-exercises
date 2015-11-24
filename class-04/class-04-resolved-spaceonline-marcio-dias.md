##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, Bulbassauro e Charmander.

# MongoDB - Aula 03 - Exercício
autor: Márcio Dias


## 1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```

> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
> var mod = { $pushAll: { moves: ['horiuken', 'Voadora'] }}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 })

> db.pokemons.find(query)
{ "_id" : ObjectId("564b1dad25337263280d047a"), "attack" : 52, "created" : "2013-11-03T15:05:41.271082", "defense" : 43, "height" : "6", "hp" : 39, "name" : "Charmander", "speed" : 65, "types" : [ "fire" ], "moves" : [ "horiuken", "Voadora" ] }
{ "_id" : ObjectId("564b1db125337263280d04a7"), "attack" : 55, "created" : "2013-11-03T15:05:41.317235", "defense" : 40, "height" : "4", "hp" : 35, "name" : "Pikachu", "speed" : 90, "types" : [ "electric" ], "moves" : [ "horiuken", "Voadora" ] }
{ "_id" : ObjectId("564b1db425337263280d04b6"), "attack" : 48, "created" : "2013-11-03T15:05:41.278310", "defense" : 65, "height" : "5", "hp" : 44, "name" : "Squirtle", "speed" : 43, "types" : [ "water" ], "moves" : [ "horiuken", "Voadora" ] }


## 2 - Adicionar 1 movimento em todos os pokemons: `desvio`.
```
> var query = {}
> var mod = {$push: {moves: 'desvio'}}
> var options = {multi: true}
> db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 610, "nUpserted" : 0, "nModified" : 610 })

> db.pokemons.find()
{ "_id" : ObjectId("564b1dad25337263280d0479"), "attack" : 56, "created" : "2013-11-03T15:05:41.305777", "defense" : 35, "height" : "3", "hp" : 30, "name" : "Rattata", "speed" : 72, "types" : [ "normal" ], "moves" : [ "desvio" ] }


## 3 - **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> var query = {name: /AindaNaoExisteMon/i};
> var mod = { $set: {"description": "Sem maiores informações"}, $setOnInsert:{ "attack": null, "defense": null, "height": null, "hp": null, "name": "AindaNaoExisteMon", "speed": null, "types": null, "moves": null }}
> var options = {upsert: true}
> db.pokemons.update(query,mod,options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564e7eac78693b810f819f21")
})
> 


## 4 - Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
{ "_id" : ObjectId("564b1dad25337263280d047a"), "attack" : 52, "created" : "2013-11-03T15:05:41.271082", "defense" : 43, "height" : "6", "hp" : 39, "name" : "Charmander", "speed" : 65, "types" : [ "fire" ], "moves" : [ "horiuken", "Voadora", "desvio", "investida", "ataque rápido" ] }
{ "_id" : ObjectId("564b1db125337263280d04a7"), "attack" : 55, "created" : "2013-11-03T15:05:41.317235", "defense" : 40, "height" : "4", "hp" : 35, "name" : "Pikachu", "speed" : 90, "types" : [ "electric" ], "moves" : [ "horiuken", "Voadora", "desvio", "investida", "ataque rápido" ] }
{ "_id" : ObjectId("564b1db425337263280d04b6"), "attack" : 48, "created" : "2013-11-03T15:05:41.278310", "defense" : 65, "height" : "5", "hp" : 44, "name" : "Squirtle", "speed" : 43, "types" : [ "water" ], "moves" : [ "horiuken", "Voadora", "desvio", "investida", "ataque rápido" ] }
{ "_id" : ObjectId("564b1de325337263280d068c"), "attack" : 49, "created" : "2013-11-03T15:05:41.260678", "defense" : 49, "height" : "7", "hp" : 45, "name" : "Bulbasaur", "speed" : 45, "types" : [ "poison", "grass" ], "moves" : [ "desvio", "investida", "ataque rápido" ] }

## 5 - Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```

> var query = {types: {$ne: 'electric'}};
> db.pokemons.find(query)
{ "_id" : ObjectId("564b1dad25337263280d0479"), "attack" : 56, "created" : "2013-11-03T15:05:41.305777", "defense" : 35, "height" : "3", "hp" : 30, "name" : "Rattata", "speed" : 72, "types" : [ "normal" ], "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "attack" : 64, "created" : "2013-11-03T15:05:41.273462", "defense" : 58, "height" : "11", "hp" : 58, "name" : "Charmeleon", "speed" : 80, "types" : [ "fire" ], "moves" : [ "desvio" ] }


## 6 - Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
> var query = {$and: [{attack: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
> db.pokemons.find(query)
> db.pokemons.find(query).count()
0


## 7 - Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 21 })
