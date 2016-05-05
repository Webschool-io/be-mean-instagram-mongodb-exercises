# MongoDB - Aula 04 - Exercício

Autor: João Paulo Costa Marra

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: /Pikachu/i}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: ['esfera elétrica', 'i
nvestida trovão']}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 12ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: /Squirtle/i}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: ['raio de gelo', 'giro rápido']}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: /Bulbasaur/i}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: /Charmander/i}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var options = {multi: true}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Jota-PC(mongod-3.2.1) be-mean-pokemons> var mod = {$setOnInsert:
                                                      {
                                                        name: 'AindaNaoExisteMon',
                                                        type: null,
                                                        attack: null,
                                                        defense: null,
                                                        height: null,
                                                        description: 'Sem maiores informações'
                                                      }
                                                  }
Jota-PC(mongod-3.2.1) be-mean-pokemons> var options = {upsert: true}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b8ffca0c0dd5daab6897d7")
})
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /esfera el
étrica/i]}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 7ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$all: [/investida trovão/i, /esfera elétrica/i]}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 7ms
```

## Pesquisar todos os pokemons que não são do tipo elétrico.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c1"),
  "name": "Charmander",
  "description": "Lagartixa isqueiro",
  "type": "fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "moves": [
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c2"),
  "name": "Squirtle",
  "description": "Tartaruga das bolhas",
  "type": "água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "moves": [
    "raio de gelo",
    "giro rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c3"),
  "name": "Pidgey",
  "description": "Passarinho nervoso",
  "type": "normal",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c4"),
  "name": "Bulbasaur",
  "description": "Sapinho dos chicotes",
  "type": "grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "moves": [
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8ffca0c0dd5daab6897d7"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 5 record(s) in 28ms
```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
```