# MongoDB - Aula 04 - Exercício

autor: Edno Fedulo

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['investida','ataque rápido']}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opt = {multi:true}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fd030b954996d30f490d7"),
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
  "_id": ObjectId("564fd047b954996d30f490d8"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
{
  "_id": ObjectId("564fd061b954996d30f490d9"),
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
{
  "_id": ObjectId("564fd076b954996d30f490da"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido"
  ]
}
Fetched 4 record(s) in 3ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opt = {multi:true}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 10 existing record(s) in 3ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee65"),
  "name": "Diglett",
  "attack": 55,
  "defense": 25,
  "height": 0.2,
  "description": "Diglett are raised in most farms. The reason is simple— wherever this Pokémon burrows, the soil is left perfectly tilled for planting crops. This soil is made ideal for growing delicious vegetables.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee66"),
  "name": "Machop",
  "attack": 80,
  "defense": 50,
  "height": 0.8,
  "description": "Machop's muscles are special—they never get sore no matter how much they are used in exercise. This Pokémon has sufficient power to hurl a hundred adult humans.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee67"),
  "name": "Butterfree",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee68"),
  "name": "Nidoran",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "description": "alterando descricao",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee69"),
  "name": "Bellsprout",
  "attack": 75,
  "defense": 35,
  "height": 0.7,
  "description": "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. ",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee6a"),
  "name": "Kingler",
  "attack": 130,
  "defense": 115,
  "height": 1.3,
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "descriptio": "descricao alterada",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd030b954996d30f490d7"),
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
  "_id": ObjectId("564fd047b954996d30f490d8"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd061b954996d30f490d9"),
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
  "_id": ObjectId("564fd076b954996d30f490da"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 10 record(s) in 5ms

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, defense: null}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opt = {upsert: true}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564fd2dc8ccd1b37744bcbd6")
})
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fd2dc8ccd1b37744bcbd6"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null
}
Fetched 1 record(s) in 1ms

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/ataque rápido/i, /investida/i]}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fd030b954996d30f490d7"),
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
  "_id": ObjectId("564fd047b954996d30f490d8"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd061b954996d30f490d9"),
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
  "_id": ObjectId("564fd076b954996d30f490da"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/ataque rápido/i, /investida/i, /desvio/i]}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee65"),
  "name": "Diglett",
  "attack": 55,
  "defense": 25,
  "height": 0.2,
  "description": "Diglett are raised in most farms. The reason is simple— wherever this Pokémon burrows, the soil is left perfectly tilled for planting crops. This soil is made ideal for growing delicious vegetables.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee66"),
  "name": "Machop",
  "attack": 80,
  "defense": 50,
  "height": 0.8,
  "description": "Machop's muscles are special—they never get sore no matter how much they are used in exercise. This Pokémon has sufficient power to hurl a hundred adult humans.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee67"),
  "name": "Butterfree",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee68"),
  "name": "Nidoran",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "description": "alterando descricao",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee69"),
  "name": "Bellsprout",
  "attack": 75,
  "defense": 35,
  "height": 0.7,
  "description": "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. ",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee6a"),
  "name": "Kingler",
  "attack": 130,
  "defense": 115,
  "height": 1.3,
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "descriptio": "descricao alterada",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd030b954996d30f490d7"),
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
  "_id": ObjectId("564fd047b954996d30f490d8"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd061b954996d30f490d9"),
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
  "_id": ObjectId("564fd076b954996d30f490da"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 10 record(s) in 5ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne: 'elétrico'}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee65"),
  "name": "Diglett",
  "attack": 55,
  "defense": 25,
  "height": 0.2,
  "description": "Diglett are raised in most farms. The reason is simple— wherever this Pokémon burrows, the soil is left perfectly tilled for planting crops. This soil is made ideal for growing delicious vegetables.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee66"),
  "name": "Machop",
  "attack": 80,
  "defense": 50,
  "height": 0.8,
  "description": "Machop's muscles are special—they never get sore no matter how much they are used in exercise. This Pokémon has sufficient power to hurl a hundred adult humans.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee67"),
  "name": "Butterfree",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee68"),
  "name": "Nidoran",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "description": "alterando descricao",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee69"),
  "name": "Bellsprout",
  "attack": 75,
  "defense": 35,
  "height": 0.7,
  "description": "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. ",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56436b31e560d128cc56ee6a"),
  "name": "Kingler",
  "attack": 130,
  "defense": 115,
  "height": 1.3,
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "descriptio": "descricao alterada",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd030b954996d30f490d7"),
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
  "_id": ObjectId("564fd047b954996d30f490d8"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd061b954996d30f490d9"),
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
  "_id": ObjectId("564fd076b954996d30f490da"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fd2dc8ccd1b37744bcbd6"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null
}
Fetched 11 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$gt: 49}}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```

