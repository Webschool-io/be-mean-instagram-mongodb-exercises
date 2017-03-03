# MongoDB - Aula 04 - Exercício

autor: Bruno Lima da Silva

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'},{name: 'Squirtle'},{name: 'Bulbassauro'},{name: 'Charmander'}]}

var query = {name: /pikachu/i}
var query = {name: /squirtle/i}
var query = {name: /Bulbassauro/i}
var query = {name: /Charmander/i}

blsrocks(mongod-3.2.8) be-mean-pokemons> var mod = {$set: {moves: ['attack 1', 'attack 2']}}

blsrocks(mongod-3.2.8) be-mean-pokemons> var options = {multi: true}

blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 3
})
```
## 2. Adicionar 1 movimento em todos os pokemons: desvio.
```js
blsrocks(mongod-3.2.8) be-mean-test> var query = {}
blsrocks(mongod-3.2.8) be-mean-test> var options = {multi: true}
blsrocks(mongod-3.2.8) be-mean-test> var mod = {$push: {moves: 'desvio'}}
blsrocks(mongod-3.2.8) be-mean-test> mod
{
  "$push": {
    "moves": "desvio"
  }
}
blsrocks(mongod-3.2.8) be-mean-test> db.pokemons.update(query,mod,options)
Updated 8 existing record(s) in 3ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```
## 3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

blsrocks(mongod-3.2.8) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, height: null, moves: null, description: "Sem maiores informações"}}

blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 72ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("57b0fe15a5afffa909f7bb21")
})
```
## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /attack 1/i]}}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 6 record(s) in 7ms
```
## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {moves: {$all: [/investida/i, /desvio/i]}}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
```
## 6. Pesquisar todos os pokemons que não são do tipo elétrico.
```js
blsrocks(mongod-3.2.8) be-mean-test> var query = {type: {$not: /elétrico/i}}
blsrocks(mongod-3.2.8) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("57af68c892ac5d57da5217b0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57af690492ac5d57da5217b1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("57af690f92ac5d57da5217b2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("57af692092ac5d57da5217b3"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57af6a5692ac5d57da5217b5"),
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
  "_id": ObjectId("57b0da5cf15f2e45389bdad7"),
  "description": "Pokemon de teste chatao",
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
  "_id": ObjectId("57b0e54aa5afffa909f7bb1f"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57b0e635a5afffa909f7bb20"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 8 record(s) in 10ms
```
## 7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```js
blsrocks(mongod-3.2.8) be-mean-test> var query = {$and: [{moves: {$in: 'investida'}}, {defense: {$not: {$lte: 49}}}]}


blsrocks(mongod-3.2.8) be-mean-test> db.pokemon.find(query)
Fetched 0 record(s) in 1ms
```
## 8. Remova todos os pokemons do tipo água e com attack menor que 50.
```js
blsrocks(mongod-3.2.8) be-mean-test> var query = {$and: [{type: 'água'}, {attack: {$lt: 50}}]}
blsrocks(mongod-3.2.8) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("57af698692ac5d57da5217b4"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba"
  ]
}
Fetched 1 record(s) in 2ms
blsrocks(mongod-3.2.8) be-mean-test> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```