# MongoDB - Aula 02 - Exercício
autor: FERNANDO MIRANDA VAZ

## Listagem das databases (passo 2)
noteblook(mongod-3.0.7) be-mean-pokemon> show dbs
be-mean         → 0.078GB
be-mean-pokemon → 0.078GB
local           → 0.078GB


## Listagem das coleções (passo 3)
noteblook(mongod-3.0.7) be-mean-pokemon> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB


## Cadastro dos pokemons (passo 4)

noteblook(mongod-3.0.7) be-mean-pokemon> var pokemon = {'name':'Pikachu', 'description':'Rato que da choque','type':'eletric', attack: 55, defense: 40, height: 0.4}
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(pokemon)
Inserted 1 record(s) in 416ms
WriteResult({
  "nInserted": 1
})

noteblook(mongod-3.0.7) be-mean-pokemon> var pokemon = {'name':'Onyx', 'description':'Minhoca de pedra','type':'rock', attack: 65, defense: 55, height: 0.4}
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

noteblook(mongod-3.0.7) be-mean-pokemon> var pokemon = {'name':'Charmander', 'description':'Lagarto de fogo','type':'fire', attack: 45, defense: 40, height: 0.7}
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

noteblook(mongod-3.0.7) be-mean-pokemon> var pokemon = {'name':'Gyarados', 'description':'Evolução do inútil','type':'', attack: 75, defense: 85, height: 2.2}
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

noteblook(mongod-3.0.7) be-mean-pokemon> var pokemon = {'name':'Magikarp', 'description':'Splash','type':'water', attack: 10, defense: 10, height: 0.9}
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})


## Lista dos pokemons (passo 5)
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("5665c2c205f1ba87c05fcfb6"),
  "name": "Pikachu",
  "description": "Rato dos relampagos",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("5665c40205f1ba87c05fcfb7"),
  "name": "Onyx",
  "description": "Minhoca de pedra",
  "type": "rock",
  "attack": 65,
  "defense": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5665c43b05f1ba87c05fcfb8"),
  "name": "Charmander",
  "description": "Lagarto de fogo",
  "type": "fire",
  "attack": 45,
  "defense": 40,
  "height": 0.7
}
{
  "_id": ObjectId("5665c47c05f1ba87c05fcfb9"),
  "name": "Gyarados",
  "description": "Evolução do inútil",
  "type": "",
  "attack": 75,
  "defense": 85,
  "height": 2.2
}
{
  "_id": ObjectId("5665c4a805f1ba87c05fcfba"),
  "name": "Magikarp",
  "description": "Splash",
  "type": "water",
  "attack": 10,
  "defense": 10,
  "height": 0.9
}
Fetched 5 record(s) in 6ms


## Pikachu (passo 6)
noteblook(mongod-3.0.7) be-mean-pokemon> var query = {name: 'Pikachu'}
noteblook(mongod-3.0.7) be-mean-pokemon> var poke = db.pokemons.find(query)
noteblook(mongod-3.0.7) be-mean-pokemon> poke.description = 'Lord of thunder'
Lord of thunder
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(poke)


## Atualização do Pikachu (passo 6)
noteblook(mongod-3.0.7) be-mean-pokemon> db.pokemons.find({name:'Pikachu'})
{
  "_id": ObjectId("5665c2c205f1ba87c05fcfb6"),
  "name": "Pikachu",
  "description": "Lord of thunder",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
