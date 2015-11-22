Aula 4 exercicio, matheus jose krumenauer weber

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
> var query = {$or : [{name : /pikachu/i}, {name : /squirtle/i}, {name: /bulbassauro/i}, {name : /charmander/i}]}
> var mod = {$pushAll : {moves : ['patada', 'endurecer']}}
> var opts = {multi : true}
> db.pokemons.update(query,mod,opts)
WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
> var query = {}
> var mod = {$push : {moves : ['desvio']}}
> var opt = {multi: true}
> db.pokemons.update(query,mod,opt)
WriteResult({ "nMatched" : 9, "nUpserted" : 0, "nModified" : 9 })

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
> var query = {name : /AindaNaoExisteMon/i}
> var mod = { $setOnInsert: {  name: "AindaNaoExisteMon"
...   , attack: null
...   , height: null
...   , defense: null
...   , moves: []
...   , description: "Sem maiores informações"
... }};
> var opts = {upsert:true}
> db.pokemons.update(query,mod,opts)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("564d1319ae96947d6331b96a")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
var query = {moves: {$in : ['investida', 'patada']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10d858ed05ea2e341135"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341136"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341137"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341138"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
var query = {moves: {$in :  ['endurecer']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10d858ed05ea2e341135"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341136"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341137"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341138"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }

```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
> var query = {moves: {$in : ['investida', 'patada']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10d858ed05ea2e341135"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341136"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341137"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341138"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
> var query = {moves: {$in :  'endurecer']}}
2015-11-18T22:10:52.122-0200 E QUERY    SyntaxError: Unexpected token ]
> var query = {moves: {$in :  ['endurecer']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10d858ed05ea2e341135"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341136"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341137"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341138"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
> var query = {type : {$ne:"elétrico"}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56478343771dc8af7806b25e"), "name" : "Charmander", "description" : "Salamandra de fogo", "type" : "fire", "attack" : 60, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("56478345771dc8af7806b25f"), "name" : "Charmeleon", "description" : "Salamandra de fogo evoluida", "type" : "fire", "attack" : 100, "height" : 5.2, "moves" : [ [ "desvio" ] ] }
{ "_id" : ObjectId("56478346771dc8af7806b260"), "name" : "Charizard", "description" : "Salamandra de fogo evoluida suprema", "type" : "fire", "attack" : 160, "height" : 17, "moves" : [ [ "desvio" ] ] }
{ "_id" : ObjectId("56478348771dc8af7806b261"), "name" : "Mewtwo", "description" : "O senhor supremo do mundo pokemon", "type" : "psychic", "attack" : 130, "height" : 5, "moves" : [ [ "desvio" ] ] }
{ "_id" : ObjectId("5647834a771dc8af7806b262"), "name" : "Mew", "description" : "Pequeninho e bonitinho", "type" : "psychic", "attack" : 110, "height" : 0.3, "moves" : [ [ "desvio" ] ] }
{ "_id" : ObjectId("564d10d858ed05ea2e341135"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341136"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341137"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d10f258ed05ea2e341138"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "patada", "endurecer", [ "desvio" ] ] }
{ "_id" : ObjectId("564d1319ae96947d6331b96a"), "name" : "AindaNaoExisteMon", "attack" : null, "height" : null, "defense" : null, "moves" : [ ], "description" : "Sem maiores informações" }

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```javascript
 var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]};
> db.pokemons.find(query)

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```javascript
var query = {$and:[ { type : "água"}, {attack:{$lt:50}}]}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })

```
