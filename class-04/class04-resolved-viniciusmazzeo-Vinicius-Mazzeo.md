# MongoDb - Aula 04 - Exercício
autor Vinicius Mazzeo

## Adicionar 2 ataques ao mesmo tempo(passo 1)

```
 var query = {name: /pikachu/i}
 var attacks = ['Ataque Relampango', 'ataque rápido', 'choque do trovão']
 var mod = {$pushAll: {moves: attacks}}

db.pokemons.update(query, mod)

Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("56aab60325214ae4c33db931"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Ataque Relampango",
    "ataque rápido"
  ],
  "active": false
}


var query = {name: /squirtle/i}
var attacks = ['Jato de água', 'ataque rápido', 'hidro bomba']
var mod = {$pushAll: {moves: attacks}}

db.pokemons.update(query, mod)

Updated 1 existing record(s) in 2ms
WriteResult({
"nMatched": 1,
"nUpserted": 0,
"nModified": 1
})

 db.pokemons.find(query)
{
  "_id": ObjectId("56aab62725214ae4c33db934"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "hidro bomba",
    "Jato de água",
    "ataque rápido"
  ]
}


var query = {name: /bulbassauro/i}
var attacks = ['Folhas Navalhas', 'Chicote de sipó', 'folha navalha']
var mod = {$pushAll: {moves: attacks}}

db.pokemons.update(query, mod)

Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("56aab61325214ae4c33db932"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "folha navalha",
    "Folhas Navalhas",
    "Chicote de sipó"
  ]
}

var query = {name: /charmander/i}
var attacks = ['Arranhão', 'Turbilhão de fogo', 'lança-chamas']
var mod = {$pushAll: {moves: attacks}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
db.pokemons.find(query)
{
  "_id": ObjectId("56aab61d25214ae4c33db933"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de foquinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "lança-chamas",
    "Arranhão",
    "Turbilhão de fogo"
  ]
}



```
## Adicionar um movimento em todos os pokemons(passo 2)

```
var query = {}
var attacks = ['Desvio']
var mod = {$pushAll: {moves: attacks}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

```
## Adicionar o pokemons AindaNaoExistemon(passo 3)

```
var query = {name: "AindaNaoExistemon"}
var mod = {$set: {active: true}, $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem Maiores informações", moves: [null]}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 58ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b62466e6b2a75bd39117e8")
})


```

## Listagem Pokemons com ataque investida e mais um ataque(passo 4)

```

var query = {moves: {$in: [/investida/i, /lança-chamas/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56aab61d25214ae4c33db933"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de foquinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Descio",
    "Arranhão",
    "Turbilhão de fogo",
    "lança-chamas",
    "Investida"
  ]
}

```

## Listagem dos pokemons com ataques que adicionei(passo 5)

```
var query = {moves: {$all: [/arranhão/i, /turbilhão de fogo/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56aab61d25214ae4c33db933"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de foquinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Descio",
    "Arranhão",
    "Turbilhão de fogo",
    "lança-chamas",
    "Investida"
  ]
}


```
## Listagem dos pokemons com ataques que adicionei(passo 7)

```
var query = {type: {$ne: "eletric"}}
db.pokemons.find(query)

```

## Listagem dos pokemons com ataques investida(passo 7)

```
var query = {$and:[ {moves: {$in: [/investida/i]}}, {defense: {$not: {$gte: 49}}}]}

db.pokemons.find(query)
{
  "_id": ObjectId("56aab60325214ae4c33db931"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Descio",
    "Ataque Relampango",
    "ataque rápido",
    "choque do trovão",
    "Investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56aab61325214ae4c33db932"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Descio",
    "Folhas Navalhas",
    "Chicote de sipó",
    "folha navalha",
    "Investida"
  ]
}
{
  "_id": ObjectId("56aab61d25214ae4c33db933"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de foquinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Descio",
    "Arranhão",
    "Turbilhão de fogo",
    "lança-chamas",
    "Investida"
  ]
}
{
  "_id": ObjectId("56aab62725214ae4c33db934"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.4,
  "active": false,
  "moves": [
    "Descio",
    "Jato de água",
    "ataque rápido",
    "hidro bomba",
    "Investida"
  ]
}
{
  "_id": ObjectId("56aabd5125214ae4c33db935"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "Descio",
    "Investida"
  ]
}
{
  "_id": ObjectId("56ae8248f04a3367ea761484"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7,
  "active": false,
  "moves": [
    "Descio",
    "Investida"
  ]
}
{
  "_id": ObjectId("56ae9958e060ee934700605d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defebse": 8000,
  "active": false,
  "moves": [
    "Descio",
    "Investida"
  ]
}
{
  "_id": ObjectId("56b2a0ee8d58b406a046c2ac"),
  "active": false,
  "moves": [
    "Descio",
    "Investida"
  ]
}
{
  "_id": ObjectId("56b624f1e6b2a75bd39117e9"),
  "name": "AindaNaoExisteMon",
  "active": true,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem Maiores informações",
  "moves": [
    null,
    "Investida"
  ]
}

```

## Remova todos os pokemons do tipo água e com ataque menor que 50(passo 8)

```
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})


```

 