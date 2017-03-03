# MongoDB - Aula 04 - Exercício
autor: Diego Vilarinho

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

**Primeiro eu insiro a Squirtle na minha base pois ela não estava dentro da lista de pokemons que escolhi para minha base.**

```
db.pokemons.insert({"name": "Squirtle", "Description": "Tartaruga que solta jatos de água", "attack": 48, "defense": 65, "height": 0.5, "type": "água"})
Inserted 1 record(s) in 10ms
WriteResult({
  "nInserted": 1
})

```

**Agora a resposta do exercício**

```
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbasaur/i}, {name: /charmeleon/i}]}
var mod = {$pushAll: {moves: ['investida', 'recuar']}}
var options = multi: true
db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```
**Resultado**

```
db.pokemons.find({moves: {$exists: 1}})
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar"
  ]
}
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar"
  ]
}
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar"
  ]
}

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 3ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
db.pokemons.find()
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab6d7d05b19f568ad749b"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell.",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "type": "água",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "New description of Beedrill.",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "type": "inseto",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab795d05b19f568ad749d"),
  "name": "Mega Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers.",
  "attack": 40,
  "defense": 40,
  "height": 2.2,
  "type": "voador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
var query = {name: /aindanaoexistemon/i}
var mod = {$setOnInsert: {"name": "AindaNaoExisteMon", "Description": "Sem maiores informações", "attack": null, "defense": null, "height": null, "type": null, "moves": [null]}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 7ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("570c096e8ebf6638e3652208")
})
db.pokemons.find({name: /aindanaoexistemon/i})
{
  "_id": ObjectId("570c096e8ebf6638e3652208"),
  "name": "AindaNaoExisteMon",
  "Description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "moves": [
    null
  ]
}
Fetched 1 record(s) in 0ms

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```

var mod = {moves: {$in: [/investida/i, /bomba dagua/i]}}
db.pokemons.find(mod)
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab6d7d05b19f568ad749b"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell.",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "type": "água",
  "moves": [
    "desvio",
    "bomba dagua",
    "investida"
  ]
}

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```

var query = {moves: {$in: [/recuar/i, /investida/i, /bomba dagua/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab6d7d05b19f568ad749b"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell.",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "type": "água",
  "moves": [
    "desvio",
    "bomba dagua",
    "investida"
  ]
}

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```

var query = {type: {$nin: ['elétrico']}}
db.pokemons.find(query)
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "New description of Beedrill.",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "type": "inseto",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab795d05b19f568ad749d"),
  "name": "Mega Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers.",
  "attack": 40,
  "defense": 40,
  "height": 2.2,
  "type": "voador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570c096e8ebf6638e3652208"),
  "name": "AindaNaoExisteMon",
  "Description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "moves": [
    null
  ]
}
{
  "_id": ObjectId("570ab6d7d05b19f568ad749b"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell.",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "type": "água",
  "moves": [
    "desvio",
    "bomba dagua",
    "investida"
  ]
}

```

## Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```

var query = {$and: [{moves: 'investida'}, {defense: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("570be6d48bfa59c3e116a7a1"),
  "name": "Squirtle",
  "Description": "Tartaruga que solta jatos de água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "água",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```

db.pokemons.remove({$and: [{type: 'água'}, {attack: {$lt: 50}}]})
Removed 2 record(s) in 1ms
WriteResult({
  "nRemoved": 2
})

```