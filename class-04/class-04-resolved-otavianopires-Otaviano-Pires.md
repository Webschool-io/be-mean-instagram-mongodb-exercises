# MongoDB - Aula 04 - Exercício
autor: Otaviano Pires Amancio

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = { $or: [{ name: /pikachu/i },{ name: /squirtle/i },{ name: /bulbasaur/i },{ name: /charmander/i }] }
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var attacks = ['investida', 'ataque rápido']
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 9ms
WriteResult({
    "nMatched": 3,
    "nUpserted": 0,
    "nModified": 3
})
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3281"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": [,
        "choque do trovão"
        "investida",
        "ataque rápido"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3283"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": [
        "investida",
        "ataque rápido"
    ]
}
{
    "_id": ObjectId("565cfdb6b623ee1c0c2a3284"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": [
        "investida",
        "ataque rápido"
    ]
}

```

## 2. Adicionar 1 movimento em todos os pokemons: desvio.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 1ms
WriteResult({
    "nMatched": 9,
    "nUpserted": 0,
    "nModified": 9
})
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("564481fc8844881046640962"),
    "name": "Victreebel",
    "description": "Planta feia do caralho",
    "type": "grass",
    "attack": 105,
    "defense": 65,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640960"),
    "name": "Psyduck",
    "description": "Esse tem uma enxaqueca da ruim",
    "type": "water",
    "attack": 52,
    "defense": 48,
    "height": 0.8,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640961"),
    "name": "Kakuna",
    "description": "Esse é casca grossa",
    "type": "bug",
    "attack": 25,
    "defense": 50,
    "height": 0.6,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640963"),
    "name": "Slowpoke",
    "description": "Esse é bobo pra caralho",
    "type": "water",
    "attack": 65,
    "defense": 65,
    "height": 1.2,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640964"),
    "name": "Charizard",
    "description": "Eu taco fogo",
    "type": "fire",
    "attack": 84,
    "defense": 78,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3281"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": [,
        "choque do trovão"
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3282"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "defense": 49,
    "height": 0.4,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3283"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfdb6b623ee1c0c2a3284"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}

```

## 3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```

Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var mod = {
...   $setOnInsert: {
...   name: "AindaNaoExisteMon",
...   description: "Sem maiores informações",
...   type: null,
...   attack: null,
...   defense: null,
...   height: null,
...   moves: []}
... }
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("565d0b1eacb7b4b575e7c69e")
})
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("565d0b1eacb7b4b575e7c69e"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": [ ]
}

```

## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: ['investida', 'choque do trovão']}}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3281"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio",
        "choque do trovão"
    ]
}

```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['dor de cabeça', 'jato de água']}}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564481fc8844881046640960"),
    "name": "Psyduck",
    "description": "Esse tem uma enxaqueca da ruim",
    "type": "water",
    "attack": 52,
    "defense": 48,
    "height": 0.8,
    "moves": [
        "desvio",
        "dor de cabeça",
        "jato de água"
    ]
}

```

## 6. Pesquisar todos os pokemons que não são do tipo elétrico.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /electric/i}}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564481fc8844881046640962"),
    "name": "Victreebel",
    "description": "Planta feia do caralho",
    "type": "grass",
    "attack": 105,
    "defense": 65,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640960"),
    "name": "Psyduck",
    "description": "Esse tem uma enxaqueca da ruim",
    "type": "water",
    "attack": 52,
    "defense": 48,
    "height": 0.8,
    "moves": [
        "desvio",
        "dor de cabeça",
        "jato de água"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640961"),
    "name": "Kakuna",
    "description": "Esse é casca grossa",
    "type": "bug",
    "attack": 25,
    "defense": 50,
    "height": 0.6,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640963"),
    "name": "Slowpoke",
    "description": "Esse é bobo pra caralho",
    "type": "water",
    "attack": 65,
    "defense": 65,
    "height": 1.2,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640964"),
    "name": "Charizard",
    "description": "Eu taco fogo",
    "type": "fire",
    "attack": 84,
    "defense": 78,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3282"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "defense": 49,
    "height": 0.4,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3283"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfdb6b623ee1c0c2a3284"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565d0b1eacb7b4b575e7c69e"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": [ ]
}

```

## 7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3283"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3281"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio",
        "choque do trovão"
    ]
}

```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
    "nRemoved": 1
})
Otaviano-PA-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("564481fc8844881046640962"),
    "name": "Victreebel",
    "description": "Planta feia do caralho",
    "type": "grass",
    "attack": 105,
    "defense": 65,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640960"),
    "name": "Psyduck",
    "description": "Esse tem uma enxaqueca da ruim",
    "type": "water",
    "attack": 52,
    "defense": 48,
    "height": 0.8,
    "moves": [
        "desvio",
        "dor de cabeça",
        "jato de água"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640961"),
    "name": "Kakuna",
    "description": "Esse é casca grossa",
    "type": "bug",
    "attack": 25,
    "defense": 50,
    "height": 0.6,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640963"),
    "name": "Slowpoke",
    "description": "Esse é bobo pra caralho",
    "type": "water",
    "attack": 65,
    "defense": 65,
    "height": 1.2,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("564481fc8844881046640964"),
    "name": "Charizard",
    "description": "Eu taco fogo",
    "type": "fire",
    "attack": 84,
    "defense": 78,
    "height": 1.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3282"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "defense": 49,
    "height": 0.4,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3283"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("565d0b1eacb7b4b575e7c69e"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": [ ]
}
{
    "_id": ObjectId("565cfd13b623ee1c0c2a3281"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": [
        "investida",
        "ataque rápido",
        "desvio",
        "choque do trovão"
    ]
}

```