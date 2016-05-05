#MongoDB - Aula 04 - Exercício
autor: Marlom Girardi

##Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> var attacks = ['Arrotar','Peidar']

dell-marlom(mongod-3.0.9) be-mean-instagram> var mod = {$pushAll: {attacks: attacks}}

dell-marlom(mongod-3.0.9) be-mean-instagram> var options = {multi: true}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

##Adicionar 1 movimento em todos os pokemons: `desvio`.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {}

dell-marlom(mongod-3.0.9) be-mean-instagram> var mod = {$push: {moves: 'desvio'}}

dell-marlom(mongod-3.0.9) be-mean-instagram> var options = {multi: true}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 4ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

##Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}

dell-marlom(mongod-3.0.9) be-mean-instagram> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', moves: null, attack: null, defense: null, moves: null, height: null, description: 'Sem maiores informações'}}

dell-marlom(mongod-3.0.9) be-mean-instagram> var options = {upsert: true}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56c10787e0f94921e32be682")
})
```

##Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$or: [{attacks: {$in: ['vamos cantar']}}, {moves: {$in: ['investida']}}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0b0d639a0da5118e29a76"),
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
  "_id": ObjectId("56c0d4361e9e2cd2cec4fb0d"),
  "description": "Pokemon de teste",
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
  "_id": ObjectId("56c0d9ede0f94921e32be680"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 120,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0aff239a0da5118e29a74"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0b05439a0da5118e29a75"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c1096c35e3d9cd260bb0f3"),
  "name": "Dollymon",
  "description": "Sou o dollynho, seu amiguinho",
  "attack": 80,
  "defense": 100,
  "attacks": [
    "vamos cantar"
  ],
  "moves": [
    "rolar"
  ]
}
Fetched 8 record(s) in 1ms
```

##Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {attacks: {$all:['arrotar', 'peidar']}}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 120,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0aff239a0da5118e29a74"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0b05439a0da5118e29a75"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
Fetched 4 record(s) in 0ms
```

##Pesquisar todos os pokemons que não são do tipo `elétrico`.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {type: {$not: /eletric/i}}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0b0d639a0da5118e29a76"),
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
  "_id": ObjectId("56c0d4361e9e2cd2cec4fb0d"),
  "description": "Pokemon de teste",
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
  "_id": ObjectId("56c0d9ede0f94921e32be680"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 120,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0aff239a0da5118e29a74"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0b05439a0da5118e29a75"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c10787e0f94921e32be682"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": null
}
{
  "_id": ObjectId("56c1096c35e3d9cd260bb0f3"),
  "name": "Dollymon",
  "description": "Sou o dollynho, seu amiguinho",
  "attack": 80,
  "defense": 100,
  "attacks": [
    "vamos cantar"
  ],
  "moves": [
    "rolar"
  ]
}
Fetched 9 record(s) in 1ms
```

##Pesquisar todos os pokemons que tenham o ataque `investida` E tenham a defesa não menor ou igual a 49.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$and: [{moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}}}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0d4361e9e2cd2cec4fb0d"),
  "description": "Pokemon de teste",
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
  "_id": ObjectId("56c0d9ede0f94921e32be680"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 120,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "active": false,
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
{
  "_id": ObjectId("56c0aff239a0da5118e29a74"),
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
  ],
  "attacks": [
    "arrotar",
    "peidar"
  ]
}
Fetched 4 record(s) in 0ms
```

##Remova todos os pokemons do tipo água e com attack menor que 50.
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```