# MongoDB - Aula 04 - Exercício
autor: Erni Augusto Fonseca Souza - SistemaOn

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var mod = { $inc: { attack: 2}}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var options = { multi: true}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 86ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = {}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var mod = { $push: { moves: "desvio" }}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var options = { multi: true}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.update(query,mod,options)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = { nome: /AindaNaoExisteMon/i}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var mod = {
     $setOnInsert :
         {
           "active": false,
           "nome": "AindaNaoExisteMon",
           "attack": null,
           "defense": null,
           "height": null,
           "description": "Sem maiores informações",
         }
 }
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var options = { upsert: true}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e352a86f62633b599c646")
})


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = {moves: {$in: [/investida/i, /hadouken/i]}}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var field = {name: 1, type: 1, attack: 1, moves: 1, _id: 0}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query, field)
{
  "name": "Gengar",
  "type": "fantasma",
  "attack": 30,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "name": "Squirtle",
  "type": "água",
  "attack": 42,
  "moves": [
    "desvio",
    "hadouken"
  ]
}


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = {moves: {$in: [/desvio/i]}}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var field = {name: 1, type: 1, attack: 1, moves: 1, _id: 0}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query,field)
{
  "name": "Charizard",
  "type": "fogo",
  "attack": 40,
  "moves": [
    "desvio"
  ]
}
{
  "name": "Blastoise",
  "type": "água",
  "attack": 40,
  "moves": [
    "desvio"
  ]
}
{
  "name": "Meowth",
  "type": "normal",
  "attack": 20,
  "moves": [
    "desvio",
    "mata-gravata"
  ]
}
{
  "name": "Gengar",
  "type": "fantasma",
  "attack": 30,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "name": "Squirtle",
  "type": "água",
  "attack": 42,
  "moves": [
    "desvio",
    "hadouken"
  ]
}
{
  "name": "Bulbassauro",
  "type": "grama",
  "attack": 37,
  "moves": [
    "desvio",
    "heal"
  ]
}
{
  "name": "Charmander",
  "type": "fogo",
  "attack": 37,
  "moves": [
    "desvio",
    "yoga-fire"
  ]
}
{
  "name": "Pikachu",
  "type": "elétrico",
  "attack": 42,
  "moves": [
    "desvio",
    "ray-bolt"
  ]
}
{
  "name": "Raichu",
  "type": "elétrico",
  "attack": 50,
  "moves": [
    "desvio"
  ]
}


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = {type: {$ne: 'elétrico'}}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("564c686c3b3548e8824ffea0"),
  "name": "Charizard",
  "description": "Charizard voa em torno do céu em busca de adversários poderosos.",
  "type": "fogo",
  "attack": 40,
  "defense": 60,
  "heigth": 1.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564c687e3b3548e8824ffea1"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "água",
  "attack": 40,
  "defense": 60,
  "heigth": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564c68993b3548e8824ffea3"),
  "name": "Meowth",
  "description": "Meowth retira suas garras afiadas em suas patas sobre a esgueirar-se slinkily sem fazer quaisquer passos incriminatórias.",
  "type": "normal",
  "attack": 20,
  "defense": 70,
  "heigth": 0.4,
  "moves": [
    "desvio",
    "mata-gravata"
  ]
}
{
  "_id": ObjectId("564c68a63b3548e8824ffea4"),
  "name": "Gengar",
  "description": "Gengar correndo passado você, fingindo ser sua sombra.",
  "type": "fantasma",
  "attack": 30,
  "defense": 60,
  "heigth": 1.5,
  "moves": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564c6a783b3548e8824ffea6"),
  "name": "Squirtle",
  "description": "Tartaruga ninja aguática.",
  "type": "água",
  "attack": 42,
  "defense": 30,
  "heigth": 0.6,
  "moves": [
    "desvio",
    "hadouken"
  ]
}
{
  "_id": ObjectId("564c6a823b3548e8824ffea7"),
  "name": "Bulbassauro",
  "description": "Animal de planta robusto.",
  "type": "grama",
  "attack": 37,
  "defense": 35,
  "heigth": 0.8,
  "moves": [
    "desvio",
    "heal"
  ]
}
{
  "_id": ObjectId("564c6a923b3548e8824ffea8"),
  "name": "Charmander",
  "description": "Dragãozinho de fogo folgado.",
  "type": "fogo",
  "attack": 37,
  "defense": 40,
  "heigth": 0.5,
  "moves": [
    "desvio",
    "yoga-fire"
  ]
}
{
  "_id": ObjectId("564e352a86f62633b599c646"),
  "active": false,
  "nome": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual (maior ou igual)** a 49.##
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: {$not: {$lte: 49 }}}]}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$not": {
          "$lte": 49
        }
      }
    }
  ]
}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("564c68a63b3548e8824ffea4"),
  "name": "Gengar",
  "description": "Gengar correndo passado você, fingindo ser sua sombra.",
  "type": "fantasma",
  "attack": 30,
  "defense": 60,
  "heigth": 1.5,
  "moves": [
    "desvio",
    "investida"
  ]
}


## Remova **todos** os pokemons do tipo água e com attack menor que 50.
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = { $and: [ { type:'água' }, { 'attack': { $lt: 50 } } ] }
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> query
{
  "$and": [
    {
      "type": "água"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

##PESQUISANDO NO BANCO
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
{
  "_id": ObjectId("564c687e3b3548e8824ffea1"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "água",
  "attack": 40,
  "defense": 60,
  "heigth": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564c6a783b3548e8824ffea6"),
  "name": "Squirtle",
  "description": "Tartaruga ninja aguática.",
  "type": "água",
  "attack": 42,
  "defense": 30,
  "heigth": 0.6,
  "moves": [
    "desvio",
    "hadouken"
  ]
}

##Removendo
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.remove(query)
Removed 2 record(s) in 5ms
WriteResult({
  "nRemoved": 2
})

##VERIFICANDO
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> var query = { $and: [ { type:'água' }, { 'attack': { $lt: 50 } } ] }
sistemaon-VirtualBox(mongod-3.0.7) be-mean-test> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
