# MongoDB - Aula 04 - Exercício
autor: Aguinaldo Alves Barbosa Silva

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var modify = {$pushAll: {moves: ["Voadora", "Rabo de Arraia"]}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var options = {multi: true}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.update(query, modify, options)

Updated 3 existing record(s) in 12ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})



## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var modify = {$push: {moves: "desvio"}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var options = {multi: true}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.update({}, modify, options)
Updated 13 existing record(s) in 1ms

WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var modify = {$setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, height: null, active: false, description: "Sem maiores informações"}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var options = {upsert: true}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.update(query, modify, options)
Updated 1 new record(s) in 3ms

WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564be05163916c13518d4aec")
})

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /ataque 1/i]}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56429127ad5b2c885bd5cf82"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429385ad5b2c885bd5cf85"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564bcfe463916c13518d4aea"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564290bbad5b2c885bd5cf81"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429155ad5b2c885bd5cf83"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429186ad5b2c885bd5cf84"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {moves: {$in: [/ataque 1/i, /ataque 2/i]}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56429127ad5b2c885bd5cf82"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("564290bbad5b2c885bd5cf81"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429155ad5b2c885bd5cf83"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429186ad5b2c885bd5cf84"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {type: {$not: /eletric/i}}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56429127ad5b2c885bd5cf82"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429385ad5b2c885bd5cf85"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564bcfe463916c13518d4aea"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429155ad5b2c885bd5cf83"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429186ad5b2c885bd5cf84"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque 1",
    "ataque 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("564be05163916c13518d4aec"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "description": "Sem maiores informações"
}

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {$and: [{moves: {$in: ["investida"]}}, {defense: {$lte: 49}}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56429385ad5b2c885bd5cf85"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var query = {$and: [{type: "água"}, {attack: {$lt: 50}}]}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.remove(query)

Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})