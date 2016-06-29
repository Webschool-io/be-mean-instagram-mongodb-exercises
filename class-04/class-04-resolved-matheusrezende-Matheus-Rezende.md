# MongoDB - Aula 04 - Exercício

Autor: Matheus Rezende Figueira

## Adicionando duas skills aos pokemóns `Pikachu`, `Squirtle`, `Bulbassaur` e `Charmander`

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {name: { $in: [/pikachu/i, /squirtle/i, /bulbassaur/i, /charmander/i]}}
matheus(mongod-3.0.12) be-mean-instagram> var mod = {$pushAll: {moves: ['porrada', 'tontura']}}
matheus(mongod-3.0.12) be-mean-instagram> var options = {multi: true}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## Adicionando a skill `desvio` a todos os pokemóns

```
matheus(mongod-3.0.12) be-mean-instagram> var mod = {$push: {moves: "desvio"}}
matheus(mongod-3.0.12) be-mean-instagram> var query = {}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})

```

## Adicionando o pokemón `Aindanaoexistemon`, caso ele não exista

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {name: /aindanaoexistemon/i}
matheus(mongod-3.0.12) be-mean-instagram> var mod = {$set: {description: "Sem maiores informações"}, $setOnInsert: {name: 'Aindanaoexistemon', attack: null, defense: null, heigh: null, type: null}}
matheus(mongod-3.0.12) be-mean-instagram> var options = {upsert: true}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.update(query, modifier, options()
... ^C

matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.update(query, modifier, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5756ece3c1727dbbca1d6323")
})

```

## Listando todos os pokemóns que possuem as skills `investida` e `tontura`

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {moves: {$all: [/investida/i, /tontura/i]}}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c9858aa189a69976d2d50"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c9923aa189a69976d2d52"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c91dbbcdf32828867cbdf"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "height": 0.4,
  "attack": 100,
  "moves": [
    "investida",
    "choque do trovão",
    "choque do trovão",
    "choque elétrico",
    "ataque rápido",
    "bola elétrica",
    "porrada",
    "tontura",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("573c98bdaa189a69976d2d51"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
```

## Listando todos os pokemóns que possuem as skills `tontura` e `desvio`

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {moves: {$all: [/tontura/i, /desvio/i]}}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c9858aa189a69976d2d50"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c9923aa189a69976d2d52"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c91dbbcdf32828867cbdf"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "height": 0.4,
  "attack": 100,
  "moves": [
    "investida",
    "choque do trovão",
    "choque do trovão",
    "choque elétrico",
    "ataque rápido",
    "bola elétrica",
    "porrada",
    "tontura",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("573c98bdaa189a69976d2d51"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
Fetched 4 record(s) in 21ms

```

## Listando todos os pokemóns que não são do tipo `elétrico`

```
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find({type: {$ne: 'electric'}})
{
  "_id": ObjectId("573c9858aa189a69976d2d50"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c9923aa189a69976d2d52"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c9a50aa189a69976d2d53"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("573fa3273df15c243b50927a"),
  "description": "Pokemons de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57519922c1e719b08aa36be6"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informaçẽs",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("573fc3642676569e4dd21991"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("573c91dbbcdf32828867cbdf"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "height": 0.4,
  "attack": 100,
  "moves": [
    "investida",
    "choque do trovão",
    "choque do trovão",
    "choque elétrico",
    "ataque rápido",
    "bola elétrica",
    "porrada",
    "tontura",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("573c98bdaa189a69976d2d51"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "porrada",
    "tontura",
    "desvio"
  ]
}
{
  "_id": ObjectId("5756ece3c1727dbbca1d6323"),
  "description": "Sem maiores informações",
  "name": "Aindanaoexistemon",
  "attack": null,
  "defense": null,
  "heigh": null,
  "type": null
}
Fetched 9 record(s) in 5ms

```

## Listando todos os pokemóns que possuam a skill `investida` e cuja defesa não seja menor ou igual a 49

```
matheus(mongod-3.0.12) be-mean-instagram> var movesquery = {skills: {$in: [/investida/i]}}
matheus(mongod-3.0.12) be-mean-instagram> var defensequery = {defense: {$not: {$lte: 49}}}
matheus(mongod-3.0.12) be-mean-instagram> var query = {$and: [movesquery, defensequery]}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## Removendo todos os pokemóns do tipo `água` com ataque menor que 50

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {$and: [{type: /water/i},{attack: {$lt: 50}}]}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.remove(query)
Removed 0 record(s) in 32ms
WriteResult({
  "nRemoved": 1
})
```
