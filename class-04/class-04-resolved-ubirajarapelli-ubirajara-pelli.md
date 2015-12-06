# MongoDB - Aula 04 - Exercício
Autor: Ubirajara Pelli

## 1 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {name: /pikachu/i}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll:{moves: ['Ataque Rápido','Cauda de Ferro']}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 184ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {name: /squirtle/i}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['Bolhas', 'Rajada de Bolhas']}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 107ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {name: /bulbassauro/i}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['Chicote de cipó','Pó do sono']}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 45ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {name: /charmander/i}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll:{moves:['Brasas','Encarar']}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
## 2 - Adicionar 1 movimento em todos os pokemons: desvio

```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var options = {multi : true}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$push:{moves: 'desvio'}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod,options)
Updated 6 existing record(s) in 1ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
```
## 3 - Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: Sem maiores informações.
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert:
... {
... name: 'AindaNaoExisteMon',
... type: null,
... attack: null,
... defense: null,
... height: null,
... description: 'Sem maiores informações'
... }
... }
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod,options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5661fb801804d607640c520f")
})
```
## 4 - Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /choque do trovão/i]}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644be6d5af181c8ac5d1230"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "Investida",
    "Teia de inseto",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564c77320483942189b3a19f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8001,
  "defense": 7999,
  "moves": [
    "Investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Ataque Rápido",
    "Cauda de Ferro",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644be4b5af181c8ac5d122f"),
  "name": "Squirtle",
  "description": "Tartaruga que solta água",
  "type": "água",
  "attack": 48,
  "defense": 35,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Bolhas",
    "Rajada de Bolhas",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bdae3c7fe93746e4b471"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 45,
  "height": 0.4,
  "moves": [
    "Investida",
    "folha navalha",
    "Chicote de cipó",
    "Pó do sono",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bdd73c7fe93746e4b472"),
  "name": "Charmander",
  "description": "Dragão de fogo",
  "type": "fogo",
  "attack": 52,
  "defense": 40,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Brasas",
    "Encarar",
    "desvio"
  ],
  "active": false
}
Fetched 6 record(s) in 3ms
```

## 5 - Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/investida/i, /choque do trovão/i]}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Ataque Rápido",
    "Cauda de Ferro",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```

## 6 - Pesquisar todos os pokemons que não são do tipo elétrico
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {type:{$not: /elétrico/i}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644be6d5af181c8ac5d1230"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "Investida",
    "Teia de inseto",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564c77320483942189b3a19f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8001,
  "defense": 7999,
  "moves": [
    "Investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Ataque Rápido",
    "Cauda de Ferro",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644be4b5af181c8ac5d122f"),
  "name": "Squirtle",
  "description": "Tartaruga que solta água",
  "type": "água",
  "attack": 48,
  "defense": 35,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Bolhas",
    "Rajada de Bolhas",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bdae3c7fe93746e4b471"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 45,
  "height": 0.4,
  "moves": [
    "Investida",
    "folha navalha",
    "Chicote de cipó",
    "Pó do sono",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644bdd73c7fe93746e4b472"),
  "name": "Charmander",
  "description": "Dragão de fogo",
  "type": "fogo",
  "attack": 52,
  "defense": 40,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Brasas",
    "Encarar",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5661fb801804d607640c520f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 7 record(s) in 4ms
```

## 7 - Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in:['Investida']}}, {defense:{$not:{$lte: 49}}} ]}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564c77320483942189b3a19f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8001,
  "defense": 7999,
  "moves": [
    "Investida",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```
## 8 - Remova todos os pokemons do tipo água e com attack menor que 50.
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack:{$lt: 50}}]}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 62ms
WriteResult({
  "nRemoved": 1
})
```
