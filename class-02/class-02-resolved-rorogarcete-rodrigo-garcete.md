###MongoDB - Aula 02 - Exercício
Autor: Rodrigo Garcete

## Listagem das databases (passo 2)

> show dbs
local           0.078GB
be-mean         0.078GB
meanapp         0.078GB
test            0.078GB
be-mean-testes  0.078GB
admin           (empty)

## Listagem das coleções (passo 3)

> show collections
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> 

## Cadastro dos pokemons (passo 4)

rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'electric', attack: 45, height: 0.6 }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pokemon2 = {'name':'Charizard','description':'Diabo do fogo','type': 'fogo', attack: 65, height: 0.44 }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pokemon3 = {'name':'Katerpie','description':'Inseto Volador','type': 'agua', attack: 85, height: 17 }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pokemon4 = {'name':'Bolbasort','description':'Tortuga verde','type': 'fire', attack: 75, height: 11 }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pokemon5 = {'name':'Boterfly','description':'Animal Salvagem','type': 'terra', attack: 45, height: 0.58 }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 401ms
WriteResult({
  "nInserted": 1
})
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon2)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon3)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon4)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon5)
Inserted 1 record(s) in 8ms
WriteResult({
  "nInserted": 1
})


## Lista dos pokemons (passo 5)

rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564a7bd661489bd6d0c137a3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 45,
  "height": 0.6
}
{
  "_id": ObjectId("564a7bdc61489bd6d0c137a4"),
  "name": "Charizard",
  "description": "Diabo do fogo",
  "type": "fogo",
  "attack": 65,
  "height": 0.44
}
{
  "_id": ObjectId("564a7be161489bd6d0c137a5"),
  "name": "Katerpie",
  "description": "Inseto Volador",
  "type": "agua",
  "attack": 85,
  "height": 17
}
{
  "_id": ObjectId("564a7be861489bd6d0c137a6"),
  "name": "Bolbasort",
  "description": "Tortuga verde",
  "type": "fire",
  "attack": 75,
  "height": 11
}
{
  "_id": ObjectId("564a7bef61489bd6d0c137a7"),
  "name": "Boterfly",
  "description": "Animal Salvagem",
  "type": "terra",
  "attack": 45,
  "height": 0.58
}
Fetched 5 record(s) in 4ms

## Pikachu (passo 6)

rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var pikachu = {name : 'Pikachu'}
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> var poke = db.pokemons.findOne(pikachu)
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> poke
{
  "_id": ObjectId("564a7bd661489bd6d0c137a3"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 45,
  "height": 0.6
}

## Atualização do Pikachu (passo 6)

rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> poke.description = "Criatura Amarelo"
Criatura Amarelo
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

