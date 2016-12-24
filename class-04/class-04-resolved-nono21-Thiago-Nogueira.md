# MongoDB - Aula 04 - Exercício
autor: Thiago Nogueira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};
var mod = { $pushAll: { moves: ['cagar pra dentro','sebo nas canelas']}};
var options = { multi: true };
db.pokemons.update(query, mod, options);
Updated 4 existing record(s) in 20ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

db.pokemons.find(query)
{
  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("5653a31aae1c4a52b85098d8"),
  "name": "Bulbassauro",
  "description": "Pokemon com cara de papangu",
  "type": "grass",
  "attack": 49,
  "height": 0.71,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
Fetched 4 record(s) in 2ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {};
var mod = { $push: { moves: "desvio"}}
var options = { multi: true }
db.pokemons.update(query, mod, options)
Updated 6 existing record(s) in 3ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})

db.pokemons.find(query)
{
  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("564513026d17278fd3fe8fb1"),
  "name": "Buldassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
{
  "_id": ObjectId("564514956d17278fd3fe8fb4"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("5653a31aae1c4a52b85098d8"),
  "name": "Bulbassauro",
  "description": "Pokemon com cara de papangu",
  "type": "grass",
  "attack": 49,
  "height": 0.71,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas"
  ]
}
Fetched 6 record(s) in 3ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /AindaNaoExisteMon/i };
var mod = { $setOnInsert: {
    name: "AindaNaoExisteMon"
  , attack: null
  , height: null
  , defense: null
  , moves: []
  , description: "Sem maiores informações"
}};
var options = { upsert: true };
db.pokemons.update(query, mod, options);
Updated 1 new record(s) in 10ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5653a98346bfb82f55d97144")
})

var query = {}
db.pokemons.find(query)
{
  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564513026d17278fd3fe8fb1"),
  "name": "Buldassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564514956d17278fd3fe8fb4"),
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
  "_id": ObjectId("5653a31aae1c4a52b85098d8"),
  "name": "Bulbassauro",
  "description": "Pokemon com cara de papangu",
  "type": "grass",
  "attack": 49,
  "height": 0.71,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653a98346bfb82f55d97144"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 7 record(s) in 2ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $all: ['investida', /cagar pra dentro/i] }};
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $in: [/cagar pra dentro/i] }};
db.pokemons.find(query)

  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653a31aae1c4a52b85098d8"),
  "name": "Bulbassauro",
  "description": "Pokemon com cara de papangu",
  "type": "grass",
  "attack": 49,
  "height": 0.71,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = { type: { $ne: "elétrico" }};
db.pokemons.find(query)
{{
  "_id": ObjectId("564513026d17278fd3fe8fb1"),
  "name": "Buldassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564514956d17278fd3fe8fb4"),
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
  "_id": ObjectId("5653a31aae1c4a52b85098d8"),
  "name": "Bulbassauro",
  "description": "Pokemon com cara de papangu",
  "type": "grass",
  "attack": 49,
  "height": 0.71,
  "moves": [
    "cagar pra dentro",
    "sebo nas canelas",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653a98346bfb82f55d97144"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 6 record(s) in 16ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]}
Fetched 0 record(s) in 3ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]}
db.pokemons.remove(query);
Removed 1 record(s) in 23ms
WriteResult({
  "nRemoved": 1
})
```
