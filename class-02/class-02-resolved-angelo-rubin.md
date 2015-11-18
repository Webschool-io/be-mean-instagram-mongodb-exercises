# MongoDB - Aula 02 - Exercício
autor: Angelo Rogério Rubin

## Listagem das databases (passo 1)

PS C:\> mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-mongodb    0.078GB
be-mean-pokemons   0.078GB
local              0.078GB

## Listagem das coleções (passo 2)

> show collections
pokemons
system.indexes

## Cadastro dos pokemons (passo 3)

> var pokemon =  {"name":"Pikachu","description":"Rato Elétrico","type":"eletrico","attack":55,"height":0.4}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon =  {"name":"Bulbassauro","description":"O chicote estrala","type":"grama","attack":49,"height":0.4}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon =  {"name":"Charmander","description":"Taca fogo nele chessuis","type":"fogo","attack":52,"height":0.6}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon =  {"name":"Squirtle","description":"Ejeta agua","type":"agua","attack":48,"height":0.5}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon =  {"name":"Caterpie","description":"Larva lutadora","type":"inseto","attack":30,"height":0.3}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

## Lista dos pokemons (passo 4)

> db.pokemons.find()
{ "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"), "name" : "Bulbassauro", "description" : "O chicote estrala", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5644f44da2c7f2543fe0ff49"), "name" : "Charmander", "description" : "Taca fogo nele chessuis", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"), "name" : "Squirtle", "description" : "Ejeta agua", "type" : "agua", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("5644fb4a2d657aa215659583"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "eletrico", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644fd892d657aa215659584"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3 }

## Encontrar um pokemon a sua escolha (passo 5)

> var q = {name:'Caterpie'}
> var p = db.pokemons.findOne(q)
> p
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3
}

## Atualização do Pokemon escolhido (passo 5)

> p.defense = 35
35
> p
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35
}
> db.pokemons.save(p)
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
> db.pokemons.find(q)
{
  "_id": ObjectId("5644fd892d657aa215659584"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}