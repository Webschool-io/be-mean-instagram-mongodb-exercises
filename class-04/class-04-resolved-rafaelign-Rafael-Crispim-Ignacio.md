# MongoDB - Aula 04 - Exercício
autor: Rafael Crispim Ignácio

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
be-mean-instagram> var query = {name: {$in: [/bulbassauro/i, /pikachu/i, /charmander/i, /squirtle/i]}}
be-mean-instagram> var mod = {$set: {'moves': ['investida', 'ataque rápido']}}
be-mean-instagram> var options = {multi: true}
be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 14ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e15e176b20acd09f6f3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("56471e76e176b20acd09f6f4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("56471eefe176b20acd09f6f6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
Fetched 4 record(s) in 3ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
be-mean-instagram> var query = {}
be-mean-instagram> var mod = {$push: {'moves': 'desvio'}}
be-mean-instagram> var options = {multi: true}
be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 3ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e15e176b20acd09f6f3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471e76e176b20acd09f6f4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eefe176b20acd09f6f6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56472045e176b20acd09f6f7"),
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
Fetched 5 record(s) in 5ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
be-mean-instagram> var query = {name: /naoexistemon/i}
be-mean-instagram> var mod = {
    $set: {active: true},
    $setOnInsert: {
        name: 'AindaNaoExisteMon',
        type: null,
        attack: null,
        height: null,
        defense: null,
        moves: [],
        description: 'Sem maiores informações'
    }
}
be-mean-instagram> var options = {upsert: 1}
be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 8ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564bdf96fce316db91de833f")
})
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564bdf96fce316db91de833f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
be-mean-instagram> var query = {'moves': { $all: ['investida', 'desvio'] }}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e15e176b20acd09f6f3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471e76e176b20acd09f6f4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eefe176b20acd09f6f6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
be-mean-instagram> var query = {'moves': { $all: ['investida', 'ataque rápido'] }}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e15e176b20acd09f6f3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471e76e176b20acd09f6f4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eefe176b20acd09f6f6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 4 record(s) in 6ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
be-mean-instagram> var query = {'type': { $ne: 'eletric' }}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e76e176b20acd09f6f4"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eefe176b20acd09f6f6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56472045e176b20acd09f6f7"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("564bdf96fce316db91de833f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [
    "desvio"
  ],
  "description": "Sem maiores informações"
}
Fetched 5 record(s) in 7ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
be-mean-instagram> var query = {$and: [{'moves': {$in: [/investida/i]}}, {'attack': {$not: {$lte: 49}}}]}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56471e15e176b20acd09f6f3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56471eafe176b20acd09f6f5"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 2 record(s) in 2ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
be-mean-instagram> var query = {$and: [
    {'attack': {$lt: 50}},
    {'type': 'água'}
]}
be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 13ms
WriteResult({
  "nRemoved": 1
})
be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.
As diferenças são as seguintes:
- $ne: não aceita regex e é utilizado para verificação de conteudo
- $not: aceita regex e é utilizado junto a outros operadores
