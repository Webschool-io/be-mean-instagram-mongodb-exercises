# MongoDB - Aula 04 - Exercício
**Autor**: Jefferson Andrade Agostinho

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: `Pikachu`, `Squirtle`, `Bulbassaro`, `Charmander`

```
dev(mongod-3.0.7) be-mean-instagram> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]}

dev(mongod-3.0.7) be-mean-instagram> var mod = { $pushAll: { moves: ['confusão', 'ataque mágico']}}

dev(mongod-3.0.7) be-mean-instagram> var options = { multi: true }

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico"
  ]
}
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico"
  ]
}
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "confusão",
    "ataque mágico"
  ]
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "confusão",
    "ataque mágico"
  ]
}
Fetched 4 record(s) in 9ms
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`

```
dev(mongod-3.0.7) be-mean-instagram> var query = {}

dev(mongod-3.0.7) be-mean-instagram> var mod = { $push: { moves: 'desvio'}}

dev(mongod-3.0.7) be-mean-instagram> var options = { multi: true }

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 4ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644a0874d97fd165a5e4f3a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab4e4d97fd165a5e4f3b"),
  "name": "Ivysaur",
  "description": "Há um botão na parte de trás deste Pokémon.",
  "type": "grama",
  "attack": 65,
  "height": 1,
  "defense": 48,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab524d97fd165a5e4f3c"),
  "name": "Charizard",
  "description": "Cospe fogo",
  "type": "fogo",
  "attack": 85,
  "height": 1.7,
  "defense": 65,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab574d97fd165a5e4f3e"),
  "name": "Pidgeout",
  "description": "Este Pokémon tem uma plumagem deslumbrante de penas lindamente brilhantes.",
  "type": "passaro",
  "attack": 77,
  "height": 1.5,
  "defense": 68,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab594d97fd165a5e4f3f"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.",
  "type": "veneno",
  "attack": 63,
  "height": 3.5,
  "defense": 59,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab544d97fd165a5e4f3d"),
  "name": "Metapod",
  "description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "inseto",
  "attack": 45,
  "height": 0.7,
  "defense": 36,
  "moves": [
    "desvio"
  ]
}
Fetched 10 record(s) in 21ms
```

## 3. **Adicionar** o pekemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: `Sem maiores informações`

```
dev(mongod-3.0.7) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}

dev(mongod-3.0.7) be-mean-instagram> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: "Sem maiores informações", type: null, attack: null, height: null, defense: null, moves: []}}

dev(mongod-3.0.7) be-mean-instagram> var options = {upsert: true}

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 11ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564ddf58fae277d6b8e0fcfe")
})

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564ddf58fae277d6b8e0fcfe"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 1 record(s) in 6ms

```

## 4. Pesquisar **todos** os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito

```
dev(mongod-3.0.7) be-mean-instagram> var query = {moves: {$in: ['investida', 'confusão']}}

dev(mongod-3.0.7) be-mean-instagram> query
{
  "moves": {
    "$in": [
      "investida",
      "confusão"
    ]
  }
}

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
Fetched 4 record(s) in 8ms

```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```
dev(mongod-3.0.7) be-mean-instagram> var query = {moves: {$in: ['ataque mágico', 'confusão']}}

dev(mongod-3.0.7) be-mean-instagram> query
{
  "moves": {
    "$in": [
      "ataque mágico",
      "confusão"
    ]
  }
}

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56449e834d97fd165a5e4f36"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
Fetched 4 record(s) in 8ms
```

## 6. Pesquisar **todos** pokemons que não são do tipo `elétrico`

```
dev(mongod-3.0.7) be-mean-instagram> var query = { type: { $ne: "elétrico" }}

dev(mongod-3.0.7) be-mean-instagram> query
{
  "type": {
    "$ne": "elétrico"
  }
}


dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56449f5d4d97fd165a5e4f37"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 19,
  "height": 0.4,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449f924d97fd165a5e4f38"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("56449fc34d97fd165a5e4f39"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "confusão",
    "ataque mágico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644a0874d97fd165a5e4f3a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab4e4d97fd165a5e4f3b"),
  "name": "Ivysaur",
  "description": "Há um botão na parte de trás deste Pokémon.",
  "type": "grama",
  "attack": 65,
  "height": 1,
  "defense": 48,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab524d97fd165a5e4f3c"),
  "name": "Charizard",
  "description": "Cospe fogo",
  "type": "fogo",
  "attack": 85,
  "height": 1.7,
  "defense": 65,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab574d97fd165a5e4f3e"),
  "name": "Pidgeout",
  "description": "Este Pokémon tem uma plumagem deslumbrante de penas lindamente brilhantes.",
  "type": "passaro",
  "attack": 77,
  "height": 1.5,
  "defense": 68,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab594d97fd165a5e4f3f"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo.",
  "type": "veneno",
  "attack": 63,
  "height": 3.5,
  "defense": 59,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644ab544d97fd165a5e4f3d"),
  "name": "Metapod",
  "description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "inseto",
  "attack": 45,
  "height": 0.7,
  "defense": 36,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564ddf58fae277d6b8e0fcfe"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 10 record(s) in 23ms
```

## 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **e** tenham a defesa **não menor ou igual** a 49

```

dev(mongod-3.0.7) be-mean-instagram> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]}


dev(mongod-3.0.7) be-mean-instagram> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$lte": 49
      }
    }
  ]
}

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 2ms
```

## 8. Remova **todos** os pokemons do tipo água e com ataque **menor** a 50

```
dev(mongod-3.0.7) be-mean-instagram> var query = {$and: [{type: 'água'}, {attack: {$lt: 50}}]}

dev(mongod-3.0.7) be-mean-instagram> query
{
  "$and": [
    {
      "type": "água"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 6ms
WriteResult({
  "nRemoved": 1
})

dev(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 2ms
```
