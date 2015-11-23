# MongoDB - Aula 04 - Exercício
**autor:** Gabriel Scavassa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {$or : [ { name: /pikachu/i }, {name : /bulbassauro/i}, {name: /charmander/i}, {name : /squirtle/i}  ]}
var mod = {$pushAll : {moves : ['investida', 'soco'] } }
var opt = { multi : true}
db.pokemons.update(query, mod, opt)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = {$push : {moves : {'desvio'} } }
db.pokemons.update(query, mod, opt)
var opt = { multi : true}
WriteResult({ "nMatched" : 11, "nUpserted" : 0, "nModified" : 11 })
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name : /Aindanaoexistemon/i}
var mod = {$setOnInsert : { name: 'Aindanaoexistemon', description:'Sem maiores informações', type: null, attack:null, defense:null, height:null, moves:null } }
var opt = { upsert : true}
db.pokemons.update(query, mod, opt)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5650d36026a5871722e2bf97")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> var query = {$or : [ {moves : ['investida', 'soco'] }, {name : /squirtle/i} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5650cb10f59251bb7dd7f59f"), "name" : "Bulbassauro", "description" : "dinossauro de planta", "type" : "grama", "attack" : 50, "defense" : 40, "height" : 0.4, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650ced4c4208957cab74244"), "name" : "Pikachu", "description" : "rato eletrico", "type" : "eletrico", "attack" : 50, "defense" : 30, "height" : 0.4, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650cf04c4208957cab74245"), "name" : "Charmander", "description" : "red devil", "type" : "fogo", "attack" : 55, "defense" : 45, "height" : 0.9, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650cf31c4208957cab74246"), "name" : "squirtle", "description" : "tartaruga esquilo", "type" : "agua", "attack" : 45, "defense" : 55, "height" : 0.8, "moves" : [ "investida", "soco", "desvio" ] }
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
> var query = {$or : [ {moves : ['investida', 'soco', 'desvio' ] }, {name : /squirtle/i} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5650cb10f59251bb7dd7f59f"), "name" : "Bulbassauro", "description" : "dinossauro de planta", "type" : "grama", "attack" : 50, "defense" : 40, "height" : 0.4, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650ced4c4208957cab74244"), "name" : "Pikachu", "description" : "rato eletrico", "type" : "eletrico", "attack" : 50, "defense" : 30, "height" : 0.4, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650cf04c4208957cab74245"), "name" : "Charmander", "description" : "red devil", "type" : "fogo", "attack" : 55, "defense" : 45, "height" : 0.9, "moves" : [ "investida", "soco", "desvio" ] }
{ "_id" : ObjectId("5650cf31c4208957cab74246"), "name" : "squirtle", "description" : "tartaruga esquilo", "type" : "agua", "attack" : 45, "defense" : 55, "height" : 0.8, "moves" : [ "investida", "soco", "desvio" ] }
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
> var query = {$and :  [ {moves : /investida/i}, {defense :{$gte: 49 } } ] }
> db.pokemons.find(query)
{ "_id" : ObjectId("5650cf31c4208957cab74246"), "name" : "squirtle", "description" : "tartaruga esquilo", "type" : "agua", "attack" : 45, "defense" : 55, "height" : 0.8, "moves" : [ "investida", "soco", "desvio" ] }

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and : [ {type : /agua/i }, {attack :{$lt : 50} } ] }
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
```
