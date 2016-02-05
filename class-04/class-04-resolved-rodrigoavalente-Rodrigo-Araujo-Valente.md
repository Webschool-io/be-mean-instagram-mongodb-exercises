# MongoDB - Aula 04 - Exercício
Autor: Rodrigo A Valente

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokémons: Pikachu, Squirte, Bulbassauro e Charmander.

```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {
... $or: [
...          {name: /pikachu/i},
...          {name: /squirtle/i},
...          {name: /bulbassaur*/i},
...          {name: /charmander/i}
...      ]
... }
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var mod = {
... $set: {
...           moves: ['tackle', 'leer']
...       }
... }
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var options = {multi: true}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 11ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("568400b86f773a2baa57f436"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "tackle",
    "leer"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f437"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "tackle",
    "leer"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f438"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fire",
  "attach": 52,
  "height": 0.6,
  "moves": [
    "tackle",
    "leer"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f439"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "tackle",
    "leer"
  ]
}
```

## Adicionar 1 movimento em todos os pokémons: desvio,
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var options = {upsert: true, multi: true}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.update({}, mod, options)
Updated 10 existing record(s) in 2ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})
```

## Adicionar o pokémon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var mod = {
... $setOnInsert: {
...                   name: 'AindaNaoExisteMon',
...                   attack: null,
...                   type: null,
...                   description: 'Sem maiores informações'
...               }
... }
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var opt = {upsert: true}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("568419e943a159276eccdfe4")
})
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({"_id": ObjectId("568419e943a159276eccdfe4")})
{
  "_id": ObjectId("568419e943a159276eccdfe4"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "type": null,
  "description": "Sem maiores informações"
}
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {moves: {$in: [/(investida|tackle)/i, /shouryuken/i]}}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var opt = {multi: true}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query, {}, opt)
{
  "_id": ObjectId("568400b86f773a2baa57f436"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f437"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f438"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fire",
  "attach": 52,
  "height": 0.6,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f439"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568428e90a27ff8562290082"),
  "name": "Hitmonchan",
  "type": "fight",
  "description": "Boxeador monstro",
  "attack": 105,
  "height": 14,
  "moves": [
    "investida",
    "shouryuken"
  ]
}
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {moves: {$in: [/shouryuken/i]}}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var opt = {multi: true}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query, {}, opt)
{
  "_id": ObjectId("568428e90a27ff8562290082"),
  "name": "Hitmonchan",
  "type": "fight",
  "description": "Boxeador monstro",
  "attack": 105,
  "height": 14,
  "moves": [
    "investida",
    "shouryuken"
  ]
}
```

## Pesquisar todos os pokemons que não são do tipo elétrico.
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {type: {$ne: 'electric'}}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5683fe5b6f773a2baa57f430"),
  "name": "Charizard",
  "description": "Pokémon dragão de fogo, mas infelizmente não é um dragão de verdade",
  "type": "fire",
  "attack": 84,
  "height": 17,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5683fe5b6f773a2baa57f432"),
  "name": "Psyduck",
  "description": "Pato que exagerou nas drogas",
  "type": "water",
  "attack": 52,
  "height": "8",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5683fe5b6f773a2baa57f433"),
  "name": "Muk",
  "description": "Meleca de esgoto mutante",
  "type": "poison",
  "attack": 105,
  "height": 12,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5683fe5b6f773a2baa57f434"),
  "name": "Kingler",
  "description": "Ensopado de caranguejo gigante",
  "type": "water",
  "attack": 130,
  "height": 13,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f437"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f438"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fire",
  "attach": 52,
  "height": 0.6,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f439"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "tackle",
    "leer",
    "desvio"
  ]
}
{
  "_id": ObjectId("568400b86f773a2baa57f43a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "insect",
  "attack": 30,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("568419e943a159276eccdfe4"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "type": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("568428e90a27ff8562290082"),
  "name": "Hitmonchan",
  "type": "fight",
  "description": "Boxeador monstro",
  "attack": 105,
  "height": 14,
  "moves": [
    "investida",
    "shouryuken"
  ]
}
```

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual (maior ou igual) a 49.
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {moves: {$in: [/(tackle|investida)/i]}, defense: {$gt: 49}}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.
```
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> var query = {$and: [{type: 'water'}, {attack: {$lt: 50}}]}
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
rvalente/mongodb(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```