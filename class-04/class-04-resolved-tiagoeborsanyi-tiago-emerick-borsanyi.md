## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
> query
{
	"$or" : [
		{
			"name" : /pikachu/i
		},
		{
			"name" : /squirtle/i
		},
		{
			"name" : /bulbassauro/i
		},
		{
			"name" : /charmander/i
		}
	]
}
var attacks = ['choque elétrico', 'ataque rápido']
var mod = {$pushAll: {moves: attacks}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

db.pokemons.find(query)
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido" ] }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2f"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "choque elétrico", "ataque rápido" ] }
{ "_id" : ObjectId("5643a0fd0de0851ffeecb67a"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido" ] }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b30"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "choque elétrico", "ataque rápido" ] }

```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = { "multi" : true }

db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 10 })

db.pokemons.find()
{ "_id" : ObjectId("564bdb067bcd78f79e049452"), "name" : "Pidgeotto", "description" : "Garras mega foda", "type" : "Brird", "attack" : 58, "height" : 0.9, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564bdb067bcd78f79e049453"), "name" : "Kakuna", "description" : "Poderes da cevada", "type" : "cocoon", "attack" : 28, "height" : 0.7, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564bdb067bcd78f79e049454"), "name" : "Venusaur", "description" : "Meio dinossauro com água de coco pra colocar no wisk", "attack" : 60, "height" : 10.6, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049455"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049456"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "choque elétrico", "ataque rápido", "desvio" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049457"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "choque elétrico", "ataque rápido", "desvio" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e049458"), "name" : "PokeBreja", "description" : "Chicote de cerveja", "type" : "grama", "attack" : 90, "height" : 5.8, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e049459"), "name" : "PokeSkol", "description" : "Pokemon que dece redondo", "type" : "liquido redondo", "attack" : 80, "height" : 0.2, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e04945a"), "name" : "Bud", "description" : "Ejeta cerveja importada", "type" : "água que passarinho não bebe", "attack" : 150, "height" : 3.8, "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564e4193a3a594f35f0b4825"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio" ] }

```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i}
var mod = { $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}
var options = {upsert: true}

db.pokemons.update(query, mod, options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564e44e01ac18f39fc3c998b")
})

db.pokemons.find(query)
{ "_id" : ObjectId("564e44e01ac18f39fc3c998b"), "name" : "AindaNaoExisteMon", "attack" : null, "defense" : null, "height" : null, "description" : "Sem maiores informações" }

```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = {$or: [{name: /pikachu/i}, {name: /bud/i}, {name: /pokeSkol/i}, {name: /charmander/i}]}
var mod = {$push: {moves: 'investida'}}
var options = { "multi" : true }

db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

var query = {$or: [{name: /pikachu/i}, {name: /pokeSkol/i}]}
var mod = {$push: {moves: 'Fode com eles'}}

db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })

var query = {moves: {$in: ['Investida', 'Fode com eles']}}

db.pokemons.find(query)
{ "_id" : ObjectId("564bdbeb7bcd78f79e049459"), "name" : "PokeSkol", "description" : "Pokemon que dece redondo", "type" : "liquido redondo", "attack" : 80, "height" : 0.2, "moves" : [ "desvio", "investida", "Fode com eles" ] }
{ "_id" : ObjectId("564e4193a3a594f35f0b4825"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "Fode com eles" ] }


```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$in: ['Fode com eles', 'facil como voar']}}

db.pokemons.find(query)
{ "_id" : ObjectId("564bdbeb7bcd78f79e049459"), "name" : "PokeSkol", "description" : "Pokemon que dece redondo", "type" : "liquido redondo", "attack" : 80, "height" : 0.2, "moves" : [ "desvio", "investida", "Fode com eles", "corrida" ] }
{ "_id" : ObjectId("564e4193a3a594f35f0b4825"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "Fode com eles", "corrida" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049456"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "corrida", "facil como voar" ] }


```

## Pesquisar todos os pokemons que não são do tipo elétrico.

```
var query = {type: {$ne: 'electric'}}
> db.pokemons.find(query).count()
10
> db.pokemons.find(query)
{ "_id" : ObjectId("564bdb067bcd78f79e049452"), "name" : "Pidgeotto", "description" : "Garras mega foda", "type" : "Brird", "attack" : 58, "height" : 0.9, "moves" : [ "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdb067bcd78f79e049453"), "name" : "Kakuna", "description" : "Poderes da cevada", "type" : "cocoon", "attack" : 28, "height" : 0.7, "moves" : [ "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdb067bcd78f79e049454"), "name" : "Venusaur", "description" : "Meio dinossauro com água de coco pra colocar no wisk", "attack" : 60, "height" : 10.6, "moves" : [ "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049455"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049457"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e049458"), "name" : "PokeBreja", "description" : "Chicote de cerveja", "type" : "grama", "attack" : 90, "height" : 5.8, "moves" : [ "desvio", "corrida" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e049459"), "name" : "PokeSkol", "description" : "Pokemon que dece redondo", "type" : "liquido redondo", "attack" : 80, "height" : 0.2, "moves" : [ "desvio", "investida", "Fode com eles", "corrida" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e04945a"), "name" : "Bud", "description" : "Ejeta cerveja importada", "type" : "água que passarinho não bebe", "attack" : 150, "height" : 3.8, "moves" : [ "desvio", "investida", "corrida" ] }
{ "_id" : ObjectId("564e44e01ac18f39fc3c998b"), "name" : "AindaNaoExisteMon", "attack" : null, "defense" : null, "height" : null, "description" : "Sem maiores informações", "moves" : [ "corrida" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049456"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "corrida", "facil como voar" ] }

OU

var query = {type: {$not: /electric/i}}
> db.pokemons.find(query).count()
10


```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
var query = {$and: [{moves: {$in: [/investida/i]}}, {attack: {$gte: 49}}]}

db.pokemons.find(query)
{ "_id" : ObjectId("564bdbeb7bcd78f79e049459"), "name" : "PokeSkol", "description" : "Pokemon que dece redondo", "type" : "liquido redondo", "attack" : 80, "height" : 0.2, "moves" : [ "desvio", "investida", "Fode com eles", "corrida" ] }
{ "_id" : ObjectId("564bdbeb7bcd78f79e04945a"), "name" : "Bud", "description" : "Ejeta cerveja importada", "type" : "água que passarinho não bebe", "attack" : 150, "height" : 3.8, "moves" : [ "desvio", "investida", "corrida" ] }
{ "_id" : ObjectId("564e4193a3a594f35f0b4825"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "Fode com eles", "corrida" ] }
{ "_id" : ObjectId("564bdb247bcd78f79e049456"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "choque elétrico", "ataque rápido", "desvio", "investida", "corrida", "facil como voar" ] }

```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}

db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })

```
