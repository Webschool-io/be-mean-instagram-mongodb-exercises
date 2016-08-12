# MongoDB - Aula 04 - Exercício
autor: **Ronaiza Cardoso**


## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var modify = {$pushAll: {moves: ["Voadora", "Rabo de Codorna"]}}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var options = {multi: true}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.update(query, modify, options)

Updated 4 existing record(s) in 184ms

WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var mod = {$push: {moves: "Desvio"}}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var op = {multi: true}

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.update({}, mod, op)

Updated 9 existing record(s) in 2ms

WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {name: /AindaNãoExisteMon/i}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, height: null, active: false, description: "Sem maiores informações"}}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var op = {upsert: true}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod, op)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("577d56dbab80d523c7296782")
})
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {moves: {$in: [/Investida/i, /Voadora/i]}}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("577d549c6717c79810dd733b"),
  "name": "Pikachu",
  "attack": 8000,
  "defense": 700,
  "height": 2.1,
  "description": "Rato eletrico",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54cf6717c79810dd733c"),
  "name": "Squirtle",
  "attack": 300,
  "defense": 400,
  "height": 2.3,
  "description": "poke muito loko",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54f26717c79810dd733d"),
  "name": "Bulbassauro",
  "attack": 3000,
  "defense": 900,
  "height": 5,
  "description": "Dino pokemon",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d55106717c79810dd733e"),
  "name": "Charmander",
  "attack": 6000,
  "defense": 900,
  "height": 5,
  "description": "Poke charmoso",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {moves: {$in: [/desvio/i]}}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",

  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d549c6717c79810dd733b"),
  "name": "Pikachu",
  "attack": 8000,
  "defense": 700,
  "height": 2.1,
  "description": "Rato eletrico",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54cf6717c79810dd733c"),
  "name": "Squirtle",
  "attack": 300,
  "defense": 400,
  "height": 2.3,
  "description": "poke muito loko",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54f26717c79810dd733d"),
  "name": "Bulbassauro",
  "attack": 3000,
  "defense": 900,
  "height": 5,
  "description": "Dino pokemon",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d55106717c79810dd733e"),
  "name": "Charmander",
  "attack": 6000,
  "defense": 900,
  "height": 5,
  "description": "Poke charmoso",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
Fetched 9 record(s) in 138ms
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {type: {$not: /eletric/i}}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",

  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d549c6717c79810dd733b"),
  "name": "Pikachu",
  "attack": 8000,
  "defense": 700,
  "height": 2.1,
  "description": "Rato eletrico",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54cf6717c79810dd733c"),
  "name": "Squirtle",
  "attack": 300,
  "defense": 400,
  "height": 2.3,
  "description": "poke muito loko",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d54f26717c79810dd733d"),
  "name": "Bulbassauro",
  "attack": 3000,
  "defense": 900,
  "height": 5,
  "description": "Dino pokemon",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d55106717c79810dd733e"),
  "name": "Charmander",
  "attack": 6000,
  "defense": 900,
  "height": 5,
  "description": "Poke charmoso",
  "moves": [
    "Voadora",
    "Rabo de Codorna",
    "Desvio"
  ]
}
{
  "_id": ObjectId("577d56dbab80d523c7296782"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 125ms
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
MaRonaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> var query = {$and: [{type: "água"}, {attack: {$lt: 50}}]}
Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 26ms
WriteResult({
  "nRemoved": 0
})

```