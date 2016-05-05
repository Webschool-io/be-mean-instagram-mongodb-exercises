# MongoDB - Aula 02 - Exercício
autor: Janynne Gomes

## Criação de db (passo 1)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) me-mean-pokemons> use be-mean-pokemons
switched to db be-mean-pokemons
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemons> 

´´´
## Listagem das databases (passo 2)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
be-mean-db        → 0.078GB
local             → 0.078GB

´´´

## Listagem das coleções (passo 3)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-instagram> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB

´´´

## Cadastro dos pokemons (passo 4)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> var poke= {'name':'Janynne', 'description':'Developer','type':'addicted', 'attack':100, 'height':0.4}
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(poke)
Inserted 1 record(s) in 226ms
WriteResult({
  "nInserted": 1
})

janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> var poke = { "name": "Joel",   "description": "Developer",   "type": "addicted",   "attack": 100,   "height": 0.4 }
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert(poke)
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})

janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> var poke = { "name": "Davi",   "description": "Developer",   "type": "addicted",   "attack": 100,   "height": 0.4 }
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert(poke)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

 var poke = { "name": "Steve",   "description": "Developer",   "type": "addicted",   "attack": 100,   "height": 0.4 }
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.insert(poke)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


´´´

## Lista dos pokemons (passo 5)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("565d222e6a760789ad85aebb"),
  "name": "Janynne",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565d233eb2e774f487d9a2b9"),
  "name": "Joel",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565d234bb2e774f487d9a2ba"),
  "name": "Joel",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565d2378b2e774f487d9a2bb"),
  "name": "Davi",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565d2385b2e774f487d9a2bc"),
  "name": "Steve",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}
Fetched 5 record(s) in 2ms


´´´

## Pikachu (passo 6)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.findOne({'name':'Steve'})
{
  "_id": ObjectId("565d2385b2e774f487d9a2bc"),
  "name": "Steve",
  "description": "Developer",
  "type": "addicted",
  "attack": 100,
  "height": 0.4
}


´´´

## Atualização do Pikachu (passo 6)

´´´
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> var steve = db.pokemons.findOne({'name':'Steve'})

janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> steve.description = 'Filho da Janynne'
Filho da Janynne

janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) be-mean-pokemon> db.pokemons.save(steve)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


´´´