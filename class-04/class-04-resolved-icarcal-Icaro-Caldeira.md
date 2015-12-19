# MongoDB - Aula 04 - Exercício
autor: Icaro Caldeira (https://github.com/icarcal)

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {name: {$in: [/Squirtle/i, /Pikachu/i, /Charmander/i, /Bulbassauro/i]}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var params = {$pushAll: {moves:['taunt','tackle']}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var options = {multi: true}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.update(query, params, options)
Updated 4 existing record(s) in 16ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var options = {multi: true}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var params = {$push: {moves:'desvio'}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.update(query, params, options)
Updated 7 existing record(s) in 1ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {name: /AindaNaoExisteMon/i}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var params = {$setOnInsert: {name: "AindaNaoExisteMon", description:"Sem maiores informações" , type: null, attack: null, defense: null, height: null}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var options = {upsert: true}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.update(query, params, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5651f76c4b505197876f8954")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {moves: {$in: [/investida/i, /thunderbolt/i]}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5651f6384b505197876f8950"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
  "type": "eletric",
  "attack": 42,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "taunt",
    "tackle",
    "desvio",
    "investida",
    "thunderbolt"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves: {$all: [/investida/i, /thunderbolt/i]}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5651f6384b505197876f8950"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
  "type": "eletric",
  "attack": 42,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "taunt",
    "tackle",
    "desvio",
    "investida",
    "thunderbolt"
  ]
}
Fetched 1 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)
agrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5651f6384b505197876f8950"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
  "type": "eletric",
  "attack": 42,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "taunt",
    "tackle",
    "desvio",
    "investida",
    "thunderbolt"
  ]
}
Fetched 1 record(s) in 1ms
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {type: {$not: /eletric/i}}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5651f6384b505197876f894e"),
  "name": "Charmeleon",
  "description": "When it swings its burning tail, it elevates the temperature to unbearably high levels.",
  "type": "fire",
  "attack": 64,
  "defense": 58,
  "height": 0.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5651f6384b505197876f894f"),
  "name": "Charizard",
  "description": "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 0.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5651f6384b505197876f894d"),
  "name": "Charmander",
  "description": "The flame at the tip of its tail makes a sound as it burns. You can only hear it in quiet places.",
  "type": "fire",
  "attack": 40,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "taunt",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("5651f6384b505197876f8952"),
  "name": "Squirtle",
  "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 5,
  "moves": [
    "taunt",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("5651f6384b505197876f8953"),
  "name": "Bulbassauro",
  "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 2.4,
  "moves": [
    "taunt",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("5651f99e4b505197876f8957"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 7 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 30.

**Se você não tiver Pokemons com valores de `defense` então faça a query para o campo `attack`, como feito abaixo:**

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {$and: [ {moves: {$in: ['invsetida']}}, {attack: {$not: {$lte: 30}}} ]}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5651f6384b505197876f8950"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
  "type": "eletric",
  "attack": 42,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "taunt",
    "tackle",
    "desvio",
    "invsetida",
    "thunderbolt"
  ]
}
Fetched 1 record(s) in 7ms
```

## Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> var query = {$and: [ {type: /water/i}, {attack: {$lt: 50}} ]}
vagrant-ubuntu-trusty-64(mongod-3.0.7) pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 17ms
WriteResult({
  "nRemoved": 1
})
```
