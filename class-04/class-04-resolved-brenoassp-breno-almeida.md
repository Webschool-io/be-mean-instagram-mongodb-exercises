# MongoDB - Aula 04 - Exercício
Autor: Breno Almeida dos Santos Rodrigues Machado

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = { $or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}] }
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var attacks = ['investida', 'ataque-rapido']
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {moves: attacks}}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
'''

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
'''

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {name: /aindanaoexistemon/i}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, moves: null, description: "Sem maiores informações"}}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565247938c76216c58040121")
})
'''

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['ember']}}, {moves: {$in: ['investida']}} ] }
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5652382dc121f88299e24406"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio",
    "ember"
  ]
}
Fetched 1 record(s) in 1ms
'''

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['ataque-rapido']}}, {moves: {$in: ['investida']}} ] }
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5652382ac121f88299e24404"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
'''

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne: 'elétrico'}}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647ed127c289526011c473e"),
  "name": "Butterfree",
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "type": "bug/flying",
  "attack": 45,
  "height": 11,
  "defense": 50,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647ee247c289526011c473f"),
  "name": "Spearow",
  "description": "Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.",
  "type": "voador",
  "attack": 60,
  "height": 3,
  "defense": 30,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647ee967c289526011c4740"),
  "name": "Ekans",
  "description": "Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.",
  "type": "venenoso",
  "attack": 60,
  "height": 20,
  "defense": 44,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647f00d7c289526011c4742"),
  "name": "Nidoqueen",
  "description": "Nidoqueens body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.",
  "type": "venenoso",
  "attack": 92,
  "height": 13,
  "defense": 87,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24405"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24406"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio",
    "ember"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24407"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("565247938c76216c58040121"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 8 record(s) in 2ms
'''

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

'''
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}} , {defense: {$not: {$lte: 49}}} ]}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5652382ac121f88299e24404"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24405"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24406"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio",
    "ember"
  ]
}
{
  "_id": ObjectId("5652382dc121f88299e24407"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "ataque-rapido",
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
'''

## Remova **todos** os pokemons do tipo água e com attack menor que 50e##

'''
-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: 'água'}, {attack: {$lt: 50}}]}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
'''
