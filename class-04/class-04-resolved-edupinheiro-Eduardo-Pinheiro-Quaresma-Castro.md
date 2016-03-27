# MongoDB - Aula 04 - Exercício
autor: Eduardo Pinheiro Quaresma Castro

## 01 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Pikachu'}
Cybertron(mongod-3.0.9) be-mean-pokemons> var attacks = ['esfera eletrica', 'investida trovão']
Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Squirtle'}
Cybertron(mongod-3.0.9) be-mean-pokemons> var attacks = ['raio de gelo', 'giro rapido']
Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Bulbasaur'}
Cybertron(mongod-3.0.9) be-mean-pokemons> var attacks = ['raio solar', 'dança de pétalas']
Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Charmander'}
Cybertron(mongod-3.0.9) be-mean-pokemons> var attacks = ['brasas', 'encarar']
Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## 02 - Adicionar 1 movimento em todos os pokemons: 'desvio'
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {}
Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
Cybertron(mongod-3.0.9) be-mean-pokemons> var options = {multi: true}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## 03 - Adicionar o pokemon 'AindaNaoExisteMon' caso ele ainda não exista com os dados
## com o valor null e a descrição: 'Sem maiores informações'
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}

Cybertron(mongod-3.0.9) be-mean-pokemons> var mod = {$setOnInsert:{name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, type: null, active: null, description: 'Sem maiores informações'}}

Cybertron(mongod-3.0.9) be-mean-pokemons> var options = {upsert: true}

Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56ad4d4b1e1b28d9a4f2c67f")
})

Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find({"_id": ObjectId("56ad4d4b1e1b28d9a4f2c67f")})
{
  "_id": ObjectId("56ad4d4b1e1b28d9a4f2c67f"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "active": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 0ms
```

## 04 - Pesquisar todos os Pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /brasas/i]}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9067"),
  "name": "Pikachu",
  "description": "An boring eletric mouse",
  "type": "eletric",
  "attack": 120,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "esfera eletrica",
    "investida trovão"
  ],
  "active": false
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9068"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio",
    "raio solar",
    "dança de pétalas"
  ]
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd906a"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro-bomba",
    "desvio",
    "raio de gelo",
    "giro rapido"
  ]
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9069"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de tão fofinho",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio",
    "brasas",
    "encarar"
  ]
}
Fetched 4 record(s) in 1ms
```

## 05 - Pesquisar todos os Pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {moves: {$all: [/investida/i, /brasas/i]}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9069"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de tão fofinho",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio",
    "brasas",
    "encarar"
  ]
}
Fetched 1 record(s) in 0ms
```

## 06 - Pesquisar todos os pokemons que não são do tipo eletrico
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {type: {$ne: 'eletric'}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9068"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio",
    "raio solar",
    "dança de pétalas"
  ]
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd906a"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro-bomba",
    "desvio",
    "raio de gelo",
    "giro rapido"
  ]
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9069"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de tão fofinho",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio",
    "brasas",
    "encarar"
  ]
}
{
  "_id": ObjectId("56ad4d4b1e1b28d9a4f2c67f"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "description": "Sem maiores informações"
}
Fetched 4 record(s) in 3ms
```

## 07 - Pesquisar todos os pokemons que tenham o ataque 'investida' e tenham a defesa não menor ou igual a 49
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte: 49}}}]}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd906a"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro-bomba",
    "desvio",t
    "raio de gelo",
    "giro rapido"
  ]
}
Fetched 1 record(s) in 1ms
```

## 08 - Remova todos os pokemons do tipo agua e com ataque menor que 50
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {$and: [{type: 'water'}, {attack: {$lt: 50}}]}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 5ms
WriteResult({
  "nRemoved": 1
})
```

## 09 - Demonstre qual a diferença entre os operadores $ne e $not
O operador $ne (not equal) é o mesmo que o operador aritmético *diferente*. Basicamente ele procura valores que não sejam igual o valor repassado.
```js
be-mean-pokemons> var query = {type: {$ne: 'eletric'}}
be-mean-pokemons> db.pokemons.find(query)
``` Retornará os pokemons cujo tipo é **diferente** de 'eletric'.

O operador $not é o mesmo que o operador lógico *not*. Ele procura valores que atendam a condição lógica repassada.
```js
be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte: 49}}}]}
be-mean-pokemons> db.pokemons.find(query)
``` Retornará os pokemons que possuam o movimento 'investida' e possuam defesa que **não seja** menor ou igual a 49.