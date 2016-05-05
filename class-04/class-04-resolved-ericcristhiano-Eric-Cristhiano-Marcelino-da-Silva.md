# MongoDB - Aula 04 - Exercício
autor: Eric Cristhiano Marcelino da Silva

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var mod = {$pushAll : {moves: ['soco', 'chute']}}
var opts = {multi: true}
db.pokemons.update(query, mod, opts)
Updated 2 existing record(s) in 6ms
WriteResult({
  "nMatched": 2,
  "nUpserted": 0,
  "nModified": 2
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = {$push: {moves: 'desvio'}}
var opts = {multi: true}
db.pokemons.update(query, mod, opts)
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name: /AindaNaoExisteMon/i}
var mod = { $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"} }
var opts = {upsert: true}
db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 44ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5658e15b87488f0f8b03e023")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in: [/investida/i, /soco/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("564296f561b7097f40e4bb14"),
  "name": "Pikachu",
  "description": "Pokemon da água",
  "type": "water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "moves": [
    "soco",
    "chute",
  	"desvio"
  ]
}
{
  "_id": ObjectId("564296ff61b7097f40e4bb17"),
  "name": "Scizor",
  "description": "Pokemon malvado",
  "type": "bug",
  "attack": 130,
  "defense": 100,
  "height": 1.8,
  "moves": [
  	"desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5658db19add8eab7b9ed2c22"),
  "name": "Squirtle",
  "description": "Lançador de água",
  "type": "water",
  "attack": 60,
  "defense": 70,
  "height": 1.1,
  "moves": [
    "soco",
    "chute",
  	"desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in: [/chute/i, /soco/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("564296f561b7097f40e4bb14"),
  "name": "Pikachu",
  "description": "Pokemon da água",
  "type": "water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "moves": [
    "soco",
    "chute",
  	"desvio"
  ]
}
{
  "_id": ObjectId("5658db19add8eab7b9ed2c22"),
  "name": "Squirtle",
  "description": "Lançador de água",
  "type": "water",
  "attack": 60,
  "defense": 70,
  "height": 1.1,
  "moves": [
    "soco",
    "chute",
  	"desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {name: {$ne: "elétrico"}}
db.pokemons.find(query)
{
  "_id": ObjectId("564296f061b7097f40e4bb13"),
  "name": "Beedrill",
  "description": "Abelha matadora",
  "type": "poison",
  "attack": 90,
  "defense": 40,
  "height": 0.4,
  "moves": [
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564296f561b7097f40e4bb14"),
  "name": "Pikachu",
  "description": "Pokemon da água",
  "type": "water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "moves": [
    "soco",
    "chute",
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564296f961b7097f40e4bb15"),
  "name": "Mr. Mime",
  "description": "Pokemon engraçado",
  "type": "psychic",
  "attack": 45,
  "defense": 65,
  "height": 1.3,
  "moves": [
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564296fc61b7097f40e4bb16"),
  "name": "Magmar",
  "description": "Pokemon de fogo",
  "type": "fire",
  "attack": 95,
  "defense": 57,
  "height": 1.3,
  "moves": [
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564296ff61b7097f40e4bb17"),
  "name": "Scizor",
  "description": "Pokemon malvado",
  "type": "bug",
  "attack": 130,
  "defense": 100,
  "height": 1.8,
  "moves": [
    [
      "desvio"
    ],
    "investida"
  ]
}
{
  "_id": ObjectId("5658db19add8eab7b9ed2c22"),
  "name": "Squirtle",
  "description": "Lançador de água",
  "type": "water",
  "attack": 60,
  "defense": 70,
  "height": 1.1,
  "moves": [
    "soco",
    "chute",
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("5658e15b87488f0f8b03e023"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 7 record(s) in 4ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = { $and: [{moves: {$in : ["investida"]}}, {defense: { $not: {$lte: 49} }}] }
db.pokemons.find(query)
{
  "_id": ObjectId("564296ff61b7097f40e4bb17"),
  "name": "Scizor",
  "description": "Pokemon malvado",
  "type": "bug",
  "attack": 130,
  "defense": 100,
  "height": 1.8,
  "moves": [
  	"desvio",
    "investida"
  ]
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and: [{type: "water"}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
Removed 0 record(s) in 1ms
WriteResult({
  "nRemoved": 0
})
```