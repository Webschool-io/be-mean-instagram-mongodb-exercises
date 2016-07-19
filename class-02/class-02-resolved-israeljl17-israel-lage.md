
# MongoDB - Aula 02 - Exercicio
autor: ISRAEL LAGE

## Criação do database - passo 01
'''
israeljl-linux(mongod-3.2.8) test> use be-mean-pokemons
switched to db be-mean-pokemons
'''

## Listagem dos databases - passo 02
'''
israeljl-linux(mongod-3.2.8) be-mean-pokemons> show dbs
be-mean-instagram → 0.000GB
local             → 0.000GB
'''

## Listagem das colecoes - passo 03
'''
israeljl-linux(mongod-3.2.8) be-mean-pokemons> show collections
'''
## Cadastro de pokemons(incluir 5) - passo 04
'''
israeljl-linux(mongod-3.2.8) be-mean-pokemons> var pokemons = [{'name':'Charizard','description':'Dragãozão','type': 'fire', attack: 100, height: 2.5 },{'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'electric', attack: 55, height: 0.4 },{'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.4 },{'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6 },{'name':'Squirtle','description':'Ejeta água que passarinho não bebe','type': 'água', 'attack': 48, height: 0.5 }]


israeljl-linux(mongod-3.2.8) be-mean-pokemons> pokemons
[
  {
    "name": "Charizard",
    "description": "Dragãozão",
    "type": "fire",
    "attack": 100,
    "height": 2.5
  },
  {
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
  },
  {
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  },
  {
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
  },
  {
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
]

israeljl-linux(mongod-3.2.8) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 328ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

'''

## Listar os pokemons - passo 05

israeljl-linux(mongod-3.2.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("578eb74926ab7c93f76cad6a"),
  "name": "Charizard",
  "description": "Dragãozão",
  "type": "fire",
  "attack": 100,
  "height": 2.5
}
{
  "_id": ObjectId("578eb74926ab7c93f76cad6b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("578eb74926ab7c93f76cad6c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("578eb74926ab7c93f76cad6d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("578eb74926ab7c93f76cad6e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

'''

## Buscar um 'pickachu' e armazenar em uma variavel poke - passo 06

'''
israeljl-linux(mongod-3.2.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)
israeljl-linux(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("578eb74926ab7c93f76cad6a"),
  "name": "Charizard",
  "description": "Dragãozão",
  "type": "fire",
  "attack": 100,
  "height": 2.5
}

'''

## Modificar a 'description' e salvar - passo 07

'''
israeljl-linux(mongod-3.2.8) be-mean-pokemons> poke.description
Dragãozão
israeljl-linux(mongod-3.2.8) be-mean-pokemons> poke.description = "Dragãozao fodao"
Dragãozao fodao
israeljl-linux(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("578eb74926ab7c93f76cad6a"),
  "name": "Charizard",
  "description": "Dragãozao fodao",
  "type": "fire",
  "attack": 150,
  "height": 2.5
}
israeljl-linux(mongod-3.2.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
israeljl-linux(mongod-3.2.8) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("578eb74926ab7c93f76cad6a"),
  "name": "Charizard",
  "description": "Dragãozao fodao",
  "type": "fire",
  "attack": 150,
  "height": 2.5
}


'''
