# MongoDB - Aula 04 - Exercício
autor: Thiago Milani

# Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander. (passo 1)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {name: 'Squirtle'}, {name: 'Bulbassauro'}, {name: 'Charmander'}]}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var mod = {$pushAll: {moves: ['Novo ataque 1', 'Novo ataque 2']}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var options = {multi: true}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 209ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57961787641ae77b2e750b35"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Novo ataque 1",
    "Novo ataque 2"
  ],
  "active": false
}
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2"
  ]
}
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2"
  ]
}
Fetched 4 record(s) in 3ms


```

# Adicionar 1 movimento em todos os pokemons: desvio. (passo 2)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var options = {multi: true}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 11 existing record(s) in 2ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23e"),
  "name": "Raichu",
  "description": "Eletric modified",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23f"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a240"),
  "name": "Emboar",
  "description": "Fire, Fighting",
  "attack": 60,
  "defense": 30,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a241"),
  "name": "Serperior",
  "description": "Grass",
  "attack": 40,
  "defense": 40,
  "height": 3.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a242"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "height": 3.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57961184641ae77b2e750b34"),
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
  "_id": ObjectId("57961787641ae77b2e750b35"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57965b1e107b582fb9f34dd1"),
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
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
Fetched 11 record(s) in 6ms
```

# Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações". (passo 3)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', description: 'Sem maiores informações.', type: null, attack: null, height: null, active: null, moves: null}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var options = {upsert: true}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 117ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5798b10c630220d10958c46e")
})
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5798b10c630220d10958c46e"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações.",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 1 record(s) in 29ms
```

# Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito. (passo 4)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {moves: {$in: ['investida', 'Novo ataque 1']}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23e"),
  "name": "Raichu",
  "description": "Eletric modified",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23f"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a240"),
  "name": "Emboar",
  "description": "Fire, Fighting",
  "attack": 60,
  "defense": 30,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a241"),
  "name": "Serperior",
  "description": "Grass",
  "attack": 40,
  "defense": 40,
  "height": 3.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a242"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "height": 3.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57961184641ae77b2e750b34"),
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
  "_id": ObjectId("57961787641ae77b2e750b35"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57965b1e107b582fb9f34dd1"),
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
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5798b10c630220d10958c46e"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações.",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 12 record(s) in 7ms
```

# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito. (passo 5)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {moves: {$all: ["Novo ataque 1", "Novo ataque 2"]}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57961787641ae77b2e750b35"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
```

# Pesquisar todos os pokemons que não são do tipo elétrico. (passo 6)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {type: {$ne: 'electric'}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23e"),
  "name": "Raichu",
  "description": "Eletric modified",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23f"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a240"),
  "name": "Emboar",
  "description": "Fire, Fighting",
  "attack": 60,
  "defense": 30,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a241"),
  "name": "Serperior",
  "description": "Grass",
  "attack": 40,
  "defense": 40,
  "height": 3.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a242"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "height": 3.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57961184641ae77b2e750b34"),
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
  "_id": ObjectId("57965b1e107b582fb9f34dd1"),
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
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5798b10c630220d10958c46e"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações.",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 11 record(s) in 7ms
```

# Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49. (passo 7)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte: 49}}}]}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a242"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "height": 3.2,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57961184641ae77b2e750b34"),
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
  "_id": ObjectId("57961787641ae77b2e750b35"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57965b1e107b582fb9f34dd1"),
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
{
  "_id": ObjectId("57967a72641ae77b2e750b37"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("57967b67641ae77b2e750b38"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
Fetched 6 record(s) in 6ms
```

# Remova todos os pokemons do tipo água e com attack menor que 50. (passo 8)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = { $and: [ {type: /água/i}, {attack: {$lt: 50}} ] }
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57967982641ae77b2e750b36"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Novo ataque 1",
    "Novo ataque 2",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 16ms
WriteResult({
  "nRemoved": 1
})
```
